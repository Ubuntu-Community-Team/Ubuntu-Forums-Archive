---
title: "Ubuntu 10.10 Won't install"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by Kennetht09 on 2011-01-13
Hello everyone,I was previously using Ubuntu 10.4 I believe and i decided to completely wipe it off and start fresh with 10.10 and im sure your wondering why i just didn't upgrade,well i wanted to start fresh and have my hard drive completely cleaned,anyways,i burned 10.10 to a disc and ran it,and started installing and it starts copying files and near the very end it gives me an error message,but it will let me boot from the disk it just will not install,and also ubuntu 10.4 has been erased so the only way for me to use my computer at the moment is booting from the disk.is there a way to completely delete everything of the hard drive and then maybe 10.10 will install successfully?  someone please let me know how to fix this,thanks.

---

### Post by -kg- on 2011-01-13
OK, you had 10.04 installed and operating, and I assume you used the first option in the partitioning section, "Install using whole disk", which will delete all partitions and create the partitions for the new installation.

Are you sure that your installation disk download was uncorrupted?  Did you check the download file with the md5 checksum?  It might run from the disk, but possibly the installer portion was somehow corrupted.

The best way I've found to download a disk image is with a torrent.  There is built-in error checking.  Of course, that doesn't mean that you can't get a corrupted image, even from a torrent.  That's the first thing I would check.

You might want to consider making a Live USB to install from (assuming that your computer will boot to a USB device...if not, there's always the [Plop boot manager]("http://www.plop.at/en/bootmanager.html")...worked great for me).  Sometimes there are problems either with a CD burn, or a CD read...a Flash drive will eliminate that problem.

BTW...I always use [Unetbootin]("http://unetbootin.sourceforge.net/") to create my Live USBs, ***BUT***...I've had very little success with the default (first..."Distribution") method.  Rather, first download the (uncorrupted and md5 checked) image, then use the second installation method (Diskimage) method to install.  Unetbootin has always worked perfectly for me using this method.

---

### Post by Quackers on 2011-01-13
While booting from the live cd press the Esc key, choose language then you should see a screen with some options. Choose "check cd for errors" and see if any are found.

---

