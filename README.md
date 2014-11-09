[]: {{{1

    File        : README.md
    Maintainer  : Felix C. Stegerman <flx@obfusk.net>
    Date        : 2014-11-09

    Copyright   : Copyright (C) 2014  Felix C. Stegerman

[]: }}}1

## Description
[]: {{{1

  mail-config - my mutt + isync config

  * mutt (-patched) + isync (for offline IMAP sync) + gnupg2
  * config split into common (shareable) and private parts
  * examples for private parts in `priv.examples/` and `README`
  * config split into separate files
  * per-account muttrc
  * gnupg2 is used to encrypt passwords
  * switch between accounts w/ folder hooks and F2, F3, ...

### Symlinks

```bash
ln -s .../mail-config     ~/.mail
ln -s .../mail-priv       ~/.mail-priv
ln -s .mail-priv/mbsyncrc ~/.mbsyncrc
ln -s .mail/mutt/rc       ~/.muttrc
```

### Common Files

```
.../mail-config
|-- mutt
|   |-- bindings          # key bindings
|   |-- colours           # colours
|   |-- extra             # extra formats
|   |-- gpg               # gpg2 config
|   |-- hooks             # hooks
|   |-- rc                # main config
`-- priv.examples
    |-- mbsyncrc          # mysyncrc example
    `-- mutt
        |-- rc            # private muttrc example
        `-- rc.foo        # private per-account muttrc example
```

### Private Files

```
.../mail-priv
|-- mbsyncrc              # mbsync config file
|-- mutt
|   |-- aliases           # put your aliases here
|   |-- alternates        # put your alternates here
|   |-- lists             # put your mailing lists here
|   |-- mailboxes         # put your mailboxes here
|   |-- new_aliases       # mutt adds aliases here
|   |-- rc                # private muttrc
|   |-- rc.bar            # private per-account muttrc
|   |-- rc.foo
|-- signature.bar         # signature
`-- signature.foo
```

#### aliases

```
alias felix flx@obfusk.net (Felix C. Stegerman)
# ...
```

#### alternates

```
alternates @obfusk\.net$
# ...
```

#### lists

```
lists "@lists\.fsfe\.org$"
# ...
```

#### mailboxes

```
mailboxes "~/Mail/bar/Inbox"
mailboxes "~/Mail/bar/quux"
mailboxes "~/Mail/bar/qux"
mailboxes "~/Mail/foo/Inbox"
mailboxes "~/Mail/foo/baz"
mailboxes "~/Mail/local/Drafts"
```

### Encryped passwords

```bash
mkdir -p ~/.secrets
read -rsp 'password: '; echo "$REPLY" | gpg2 -e -r KEYID -o ~/.secrets/bar.gpg
read -rsp 'password: '; echo "$REPLY" | gpg2 -e -r KEYID -o ~/.secrets/foo.gpg
```

[]: }}}1

## License

  GPLv3+ [1].

## References

  [1] GNU General Public License, version 3
  --- http://www.gnu.org/licenses/gpl-3.0.html

[]: ! ( vim: set tw=70 sw=2 sts=2 et fdm=marker : )
