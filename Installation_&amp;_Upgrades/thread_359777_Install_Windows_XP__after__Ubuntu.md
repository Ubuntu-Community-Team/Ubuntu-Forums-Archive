---
title: "Install Windows XP _after_ Ubuntu?"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by gommle on 2007-02-12
I want to dual boot Ubuntu and XP, the only problem is: How do I fix grub after Windows deletes it? I've only heard that happens, so correct me if I'm wrong.

Here's my current partitions: (Just in case I need them later)
```

sda1 ext3 (Ubuntu)
sda4 linux-swap
sda2 ext3 (Will be reformated to NTFS for XP)
sda3 extended
> sda5 ext3 (Storage)

```

34 Internets for the solution :)

---

### Post by mikewhatever on 2007-02-12
You'd need to reinstall GRUB after Windows installation. Several ways to do it are outlined here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29)

---

### Post by gommle on 2007-02-12
Thanks :D

/me really wants to play Oblivion now.

---

### Post by gommle on 2007-02-13
I tried the Super Grub Disk. I couldn't fix the MBR or start Ubuntu directly...

Will try the other way today.

---

### Post by housam on 2007-02-13
You can try [this way ]("http://doc.gwos.org/index.php/Restore_Grub")too.

---

