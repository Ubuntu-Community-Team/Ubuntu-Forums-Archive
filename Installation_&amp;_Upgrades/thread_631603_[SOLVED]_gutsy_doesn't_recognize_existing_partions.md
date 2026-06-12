---
title: "[SOLVED] gutsy doesn't recognize existing partions"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by Drate on 2007-12-04
I am trying to run Ubuntu Gutsy Server as a dual-boot with PCLinuxOS 2007.   For the purposes of a CLEAN ENVIRONMENT after some bad tinkering I want to  re-install Gutsy Server.

Unfortunately, I have an IDE hard drive which the installer thinks is SCSI and existing partitions that need to stay in existence but Gutsy installer doesn't recognize them.  It's becoming rather discouraging.  Please help.

---

### Post by Drate on 2007-12-07
Why doth thou maketh me bump?

---

### Post by Pumalite on 2007-12-07
How did you install it in the first place.

---

### Post by Drate on 2007-12-08
I think I figured it out. And I SUSPECT this may be the culprit in all related bugs:

My partition table went something like this:

hda1 primary Ubuntu_Server
hda2 primary /home
hda3 extended

hda5 logical PCLinuxOS_2007
hda6 logical swap

Apparently (I wish I could find the forum post that I learned this form) extended partitions freak out some partition managers. I don't know why, but evidence supports this. I actually ended up in a Knoppix LiveCD, moved PCLOS to a directory under hda1, deleted the extended partition with fdisk (the only partition manager that could see it), then used gparted to create a two new primary partitions in it's place, moved stuff back to the new partition, reinstalled grub, fixed the fstab and menu.lst files, and BAM! It works. Suddenly all partition managers (including the Ubuntu installer) could see the partitions.

So yeah

---

