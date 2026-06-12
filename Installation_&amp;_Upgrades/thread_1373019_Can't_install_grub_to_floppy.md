---
title: "Can't install grub to floppy"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by HalfMadDad on 2010-01-05
Hi Everyone

unfortunately I have to use Win NT 4.0 everyday and in fact I am trying to create a system where I have many versions of NT on one disk. My plan is to store them in Linux and create a shell script to over write the first primarly partition which is ntfs. I am trying to install Xubuntu Koala on a logical partition and NT at the start of the disk. Grub is not loading NT well. I want to just use the NT booter and launch Linux from a floppy. 

During the install there is an option to write grub to /dev/fd0 but it won't work for me. I tried both fat and ext2 formatted disks and I made sure they were present during the initial boot for auto mounting. I have verified that the floppy drive actually works.

Please help me install grub to my floppy.

Thanks in advance-Patrick

---

### Post by dato1989 on 2010-01-05
> **HalfMadDad said:**
> Hi Everyone

unfortunately I have to use Win NT 4.0 everyday and in fact I am trying to create a system where I have many versions of NT on one disk. My plan is to store them in Linux and create a shell script to over write the first primarly partition which is ntfs. I am trying to install Xubuntu Koala on a logical partition and NT at the start of the disk. Grub is not loading NT well. I want to just use the NT booter and launch Linux from a floppy. 

During the install there is an option to write grub to /dev/fd0 but it won't work for me. I tried both fat and ext2 formatted disks and I made sure they were present during the initial boot for auto mounting. I have verified that the floppy drive actually works.

Please help me install grub to my floppy.

Thanks in advance-Patrick
you can try this links
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)
[https://help.ubuntu.com/community/Installation/WithFloppies](https://help.ubuntu.com/community/Installation/WithFloppies)
or visit [https://help.ubuntu.com/community](https://help.ubuntu.com/community) and type what are you interested about 

david

---

### Post by phillw on 2010-01-05
Hi and welcome the forums,

This excellent thread covers both grub legacy (pre 9.10) and grub2 and floppies.

[http://ubuntuforums.org/showthread.php?t=1305475](http://ubuntuforums.org/showthread.php?t=1305475)

Should get you sorted :-)

Regards,

Phill.

---

