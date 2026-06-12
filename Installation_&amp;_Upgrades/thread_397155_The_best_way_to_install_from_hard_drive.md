---
title: "The best way to install from hard drive?"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by Wielenga on 2007-03-30
Hello,

I have got vaio pcg-c1xd and try to install edgy xubuntu. Did already once using a transplant....

C1 does not have CD-ROM so I tried the hard disk method.

[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html]("http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html")

and

[http://ubuntuforums.org/archive/index.php/t-28948.html](http://ubuntuforums.org/archive/index.php/t-28948.html)

Disk layout is as follows:

partition 0 1.4G FAT 32 with ISO and files as in the howto etc ie /boot.
partition 1   4G NTFS XP just in case
partition 2  the rest unused for xubuntu

The proble I have is that the setup starts but than asks me for the CD-ROM hardware again and again.  I also seem to have problems with the ln command (fat 32 does not allow ln?)

---

### Post by zvacet on 2007-03-31
this is all I can find
[https://help.ubuntu.com/community/Installation/FromWindows]("https://help.ubuntu.com/community/Installation/FromWindows")

---

### Post by Wielenga on 2007-04-10
Yeah, I get the install to start but I am not able to loopmount HD and keeps looking for the ?dev/cdrom during the installation. the ln command does not work....

Any ideas anybody?

---

