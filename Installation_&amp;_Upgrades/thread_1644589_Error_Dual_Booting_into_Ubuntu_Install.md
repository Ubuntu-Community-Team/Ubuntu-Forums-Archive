---
title: "Error Dual Booting into Ubuntu Install"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by austaph on 2010-12-13
I just migrated my Wubi install to a dedicated partition, everything went fine except Windows is no longer showing up on my Grub boot menu.  Instead it's been replaced with Ubuntu (/dev/sda1) which is my original Wubi install.  Normally I'd tinker, but I have to be extremely precautious with my bootloader since I have no CD-ROM or USB drive - thus no reliable way of restoring my system in the event I can't boot into an OS.

---

### Post by Rubi1200 on 2010-12-13
Is this a Wubi install on a separate partition or an Ubuntu install on a dedicated partition (sorry was not sure from the post)?

The error message might have something to do with this if it is Wubi:
[https://wiki.ubuntu.com/WubiGuide#Windows%20Missing%20hal.dll]("https://wiki.ubuntu.com/WubiGuide#Windows%20Missing%20hal.dll")

EDIT: okay, I get it now about which method you used.

Here is my recommendation:
Install using Wubi and then migrate it to a dedicated partition using this excellent guide:
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

I have seen a lot of users who have done this successfully and I think it would be easier than what you are currently trying to do (in my opinion).

---

### Post by austaph on 2010-12-13
Thanks for the reply.  This isn't a Wubi installation, it's sort of a bootstrap.  The method I have to use involves 
[LIST=1]
[*]Copying the installation files to my partition root
[*]Using the Windows bootloader to boot into GRUB
[*]Using GRUB to boot into a specific kernel and begin the normal installation process
[/LIST]

My problem is that the Windows bootloader is failing to properly boot into c:\grub, and likely has to do with the way my Boot.ini is laid out.

Edit:
> Install using Wubi and then migrate it to a dedicated partition

Thanks a bunch, I think I'll just do that instead.

---

### Post by Rubi1200 on 2010-12-13
Let us know how it goes and if you have any questions feel free to ask. We are here to try and help.

Make sure to prepare the partitions you need first and to do any backups, defragmenting and so on before you start.

Good luck!

---

### Post by austaph on 2010-12-28
It's been a while, holidays and all.  I updated the first post to where I'm at currently.

---

