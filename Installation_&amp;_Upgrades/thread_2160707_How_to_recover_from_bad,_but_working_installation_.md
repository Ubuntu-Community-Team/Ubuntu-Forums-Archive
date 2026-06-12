---
title: "How to recover from bad, but working installation of 12.04"
date: 2013-07-07
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2013-07-07
I am in the process of converting my office from Win XP Pro SP3 to Ubuntu 12.04, but setting each machine for dual either by patitioning a single HD (or SSD) or using two HD.  Everything went well until I tackled my DELL Vostro 3500 laptop (has Crucial SSD).  After making copies of critical files, and an image of the Win XP partition, I used Gparted to set remaining 20 GB on the SSD to ext4.  I then tried to use the LIve CD for 12.04 64-bit since Intel(R) Core(TM) i5 CPU M 520 @ 2.40GHz is reportedly 64-bit.  Neither of my CD-ROMS for 64-bit 12.04 would load far enough to do a live session (no error messages, just Ubuntu and dots).  So I tried the 32-bit version.  Based on prior installations, I expected Ubuntu to see the 20 GB of ext4 and make a good installation.  That did not work as the install program wanted to chop the 20 GB into at least two sections (and sometimes more on installation I overwrote).  Please see gparted screenshot attached.

Since I have not done much to this installation except call up the WiFi and nVidia proprietary drivers, I can go back and do a reintallation overwriting the current Ubunto installation.  How do I get the reinstation to give me one 20GB contiguous space?  I don't need a swap file as 4 GB RAM is more than enough to do most everything.

Long-term objective is to move files gradually from Win partition to Ubuntu partitiion, gradually decreasing size of Win and increasing size of Ubuntu.

Thank you,

John

---

### Post by leosubhadeep on 2013-07-08
Did you define a swap partition and tried?

If you can, try re-installing Ubuntu from the bootable usb drive (not mandatory, though!). It is recommended to have a dedicated swap partition and (optionally) a dedicated "usr" partition, to be mounted during installation process. If you are re-installing, forget gparted's deeds and follow Ubuntu installation media's way. While partitioning use "Try something else" from the installation wizard. A bit of help here: [http://www.fosspedia.com/how-to-install-ubuntu-12-10-alongside-windows/](http://www.fosspedia.com/how-to-install-ubuntu-12-10-alongside-windows/)

---

### Post by cigtoxdoc on 2013-07-09
Thank you for your help.  I followed your instructions and partitioned the "Ubuntu area" of the drive before reinstalling 12.04.  Results are attached.

John

---

