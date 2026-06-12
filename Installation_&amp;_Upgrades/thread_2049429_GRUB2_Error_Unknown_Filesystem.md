---
title: "GRUB2 Error: Unknown Filesystem"
date: 2012-08-28
forum: Installation &amp; Upgrades
---

### Post by rockstarrem on 2012-08-28
Hey guys,

I successfully installed Ubuntu on a separate hard drive with a UEFI motherboard, and now when I boot into that drive I get a "Error: unknown filesystem" error. Can someone help me?

Also, I'm dual booting with Windows. Windows is on one drive, Ubuntu on the other.

---

### Post by rockstarrem on 2012-08-28
Alright, I got it to boot with [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/) . I selected "Detect all operating systems" and a ton of "Error: unknown filesystems" came on the screen and then eventually it came up Linux. Any ideas on how to not use this disk and have it work as normal?

---

### Post by ajgreeny on 2012-08-28
I know very little about UEFI but it is still probably worth booting to a live CD or USB, and then running the boot-info-script (see my signature below) or boot repair at [Ubuntu Boot Repair.]("http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html")

That should give a lot of information about your system and the disks/grub/boot setup etc etc.

EDIT:
Just seen your new post.  As you now have it managing to boot try [Ubuntu Boot Repair]("http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html")

That should do the trick.

---

### Post by rockstarrem on 2012-08-28
Thank you so much, it actually worked! Do you know if this works with other distro's as well if you follow the same steps (install same software and run same commands)?

---

### Post by YannBuntu on 2012-08-29
> **rockstarrem said:**
> Thank you so much, it actually worked!

Great :) Please could you indicate the URL that was provided by Boot-Repair? (if you don't remember please follow this tutorial: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) )

> **rockstarrem said:**
> Do you know if this works with other distro's as well if you follow the same steps (install same software and run same commands)?

Boot-Repair fixes Debian derivatives (Ubuntu, Mint..), but it should be able to fix also Fedora, OpenSuse, Arch.
Which distribution do you want to fix?

---

