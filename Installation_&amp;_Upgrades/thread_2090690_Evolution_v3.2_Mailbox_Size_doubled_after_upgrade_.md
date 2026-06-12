---
title: "Evolution v3.2 Mailbox Size doubled after upgrade to Ubuntu 12.04"
date: 2012-12-03
forum: Installation &amp; Upgrades
---

### Post by ozneil on 2012-12-03
I love Ubuntu and Evolution so I installed Evolution on Ubuntu 12.04 when I upgraded recently.

I restored my mail from a backup and on starting Evolution for the first time, received a message about converting my emails and once successful, deleting the mbox versions via Edit -> Preferences -> Mail accounts.

This all worked as expected until I did my first backup and realised that the backup file has doubled in size from about 2GB to 4.2GB.

My mail seems to now be stored in the following folders:

/.local/share/evolution/mail/local_mbox - 4.2 GB
/.local/share/evolution/mail/local - 27.1 MB

I am not sure where I went wrong. I am pretty sure the files were converted as it took quite a long time. Rechecking in Edit -> Preferences -> Mail accounts, I can't see any references to MBOX accounts and I remember deleting the MBOX account after my emails were onverted.

I'd really like to get my mail folders down to a more manageable size if possible if anyone has any advice?

Thanks in advance.

Neil.

---

### Post by bilkay on 2012-12-05
I THINK the local_mbox stuff is the old version that can be deleted. You might try renaming the directory and see if it causes a problem. If not, then delete it. Also, check the dates on the files. If there are none after the time you upgraded, you should be OK deleting the directory. I wish I could find something in the help to verify this, but I haven't yet.

Since upgrading, I've also encountered another problem. When I send mail, I was getting an error message:

```
The reported error was "Failed to append to mbox:///home/bilkay/.local/share/evolution/mail/local#Sent: Invalid folder URI 'mbox:///home/bilkay/.local/share/evolution/mail/local#Sent'
Appending to local 'Sent' folder instead.".
```

I had to go into my mail accounts and set the default directories for Sent and Draft messages.

---

