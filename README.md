# doveadm-adddate

Add a `Date` header to mails where it is missing

## Description

My mailbox contained some mails without a `Date` header, stored in a Dovecot IMAP Folder.
When sorting by date in my mail client, these messages didn't show up in the correct place.

To fix this, this script adds `Date` headers with dovecots internal `date.received`
timestamp.

## Usage

See what it would do:
```
sudo ./doveadm-adddate -u someuser --dry-run
```

Actually do it:
```
sudo ./doveadm-adddate -u someuser
```

## Caveats

### No Guarantees

**No warranty, use at you own risk. If you lose mail or something else goes horribly
wrong it is your responsibility alone.**

Take a backup before you use this script to modify any mailboxes.

### New mails get created and old mails will be deleted

Mails cannot be modified once they are stored, therefore this script creates a new mail
with the added `Date` header and **deletes** the old message. This sets the mail to "unread"
and clears other flags that might have been set on the mail.
