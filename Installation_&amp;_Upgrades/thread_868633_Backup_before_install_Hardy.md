---
title: "Backup before install Hardy"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by carverj on 2008-07-24
Hi,
   I am about to install Hardy Heron 64 bit desktop, and would like to backup my Gutsy personal data first in order to copy it back once complete.
Is it best to use tar for backing up /home?:

```
tar cvpzf backup.tgz /home
```

Or better to copy all:

```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```

Thanks all.

---

### Post by mikewhatever on 2008-07-24
Home is all you'd need to backup. You don't want to overwrite the new installation with old files from Gutsy, right?

---

### Post by carverj on 2008-07-28
Ok, thanks mate. Will do.
So i guess this means that all the applications I used in Gutsy and their various links and files are stored in /home !?

Thanks guys.

---

### Post by pkl266 on 2008-07-28
Yep, all the data that you need to transfer should be in /home. The stuff for the applications are in hidden folders in /home, most likely.

---

