---
title: "Multiple-boot / Partitioning?"
date: 2005-04-29
forum: Installation &amp; Upgrades
---

### Post by es012 on 2005-04-29
I have WinXP and Red Hat 9 installed on my computer, set up as a dual boot. XP is on the main 40 gig hard drive, while the secondary (80 gig) hard drive is split in half, the first half formated in NTFS, and the second half is ext3 with Red Hat. What I want to do is split the Red Hat partition into a few more partitions so I can install Ubuntu and maybe Fedora and/or Mandrake. What program should I use to split the partition in Red Hat into multiple partitions, and how do I set up the boot loader to display the other new OS's? I am new to Linux, so I am learning as I go. Any help is appreciated!
Thanks!
-
Erick

---

### Post by nad on 2005-04-30
Partition Magic is a windows executable that I have used without problems. In Red Hat you will probably find parted, fdisk, sfdisk and cfdisk. These are all command line tools. Only parted can resize an existing filesystem. QTparted and gparted are gui frontends to parted and may be available rpms if they are not already installed on your system.

Be aware that resizing file systems with these tools usually works without error, however, backing up any important data is judicious.

As far as configuring a bootloader, there are several available. What are you using now?

---

### Post by 23meg on 2005-04-30
i would avoid partition magic and use [qtparted](http://qtparted.sourceforge.net). pm occasionally causes irreversible mess with filenames when resizing partitions.

---

### Post by es012 on 2005-04-30
My boot loader is GRUB 0.93. As for the partitioning tools I looked at Partition Magic, but it costs money. I was thinking more along the lines of opensource or freeware. The QtParted program looks interesting, but I can't download the rpm. I click on the link and the next page says that it was not found. I really don't want the source file, because I don't know how to set every thing up.

---

### Post by nad on 2005-04-30
Ubuntu uses grub by default also. You should search these forums for issues and howtos to familiarize yourself with the process and prepare for the unexpected. You may wish to hand configure your existing bootloader. I find this the most effective and error-free method. Either way, make a copy of your rh /boot directory for reference and safety.

Please search the rh forums for a version of QTparted for your system.

---

### Post by mkoljack on 2005-04-30
qtparted is available as an rpm.through Red Hat.  Just do:

yum install qtparted

It will install the rpm and its dependencies.  I just did it in Fedora Core 3.

Good Luck.

---

### Post by Jenda on 2005-04-30
Is QT available for Windows?

---

### Post by momo66 on 2005-05-05
not available in Windows

---

