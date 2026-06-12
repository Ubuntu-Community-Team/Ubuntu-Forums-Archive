---
title: "Problem with booting lubuntu on partition formatted in F2FS"
date: 2020-04-09
forum: Installation &amp; Upgrades
---

### Post by rororox on 2020-04-09
Hello, 

I recently installed Lubuntu distro on partition formatted in F2FS, to play with it, but something gone wrong, and I need to boot the system manually from GRUB 2.04 using:

```
grub> set prefix=<(hd0,gpt2)/grub
grub> set root=(hd0,gpt2)
grub> insmod linux
grub> insmod normal
grub> normal

```

Here is log from boot-info
[https://paste.ubuntu.com/p/KK7j2z4c9X/](https://paste.ubuntu.com/p/KK7j2z4c9X/)

---

### Post by yancek on 2020-04-09
Your boot repair output does not show a lot of the information generally included in the report.  Not sure if that is because of the device but not having a grub.cfg file is definitely a problem.  It does show an efi partition and efibootmgr shows an entry for Ubuntu.  You could try mounting  /dev/mmcblk0p1 to see if it has the appropriate efi files and also mount  /dev/mmcblk0p2 to see if it has the required boot files such as Grub and grub.cfg.  Don't know anything about the filesystem you are using.

---

### Post by oldfred on 2020-04-09
Boot-Repair uses the older script bootinfoscript for first part of report.
And both NVMe drives & MMC drives are not yet included in the old bootinfoscript.

there are two different versions with some NVMe data, but none published.
Nether fully work.
[https://github.com/arvidjaar/bootinfoscript/issues/5](https://github.com/arvidjaar/bootinfoscript/issues/5)

---

