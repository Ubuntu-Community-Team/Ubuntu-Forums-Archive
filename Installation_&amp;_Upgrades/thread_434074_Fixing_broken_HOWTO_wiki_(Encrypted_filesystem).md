---
title: "Fixing broken HOWTO wiki (Encrypted filesystem)"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by bck on 2007-05-05
I've been trying to follow the HOWTO for installing feisty from scratch to an encrypted root/swap:  [https://help.ubuntu.com/community/EncryptedFilesystemHowto6](https://help.ubuntu.com/community/EncryptedFilesystemHowto6)

So far I've still not yet gotten it to work, so I'd like to figure out what's wrong and then fix the page.  Issues I've found so far:

[LIST=1]
[*]Need to aptitude install debootstrap
[*]Need to mount --bind /dev to the chrooted environment
[/LIST]

Now when I boot up I don't get asked for a password, but I do get:
```

Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/mapper/root does not exist!  dropping to a shell

```

And then get dropped to the busybox shell.

Any ideas?

Thanks

---

