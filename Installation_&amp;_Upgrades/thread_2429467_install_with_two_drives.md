---
title: "install with two drives"
date: 2019-10-18
forum: Installation &amp; Upgrades
---

### Post by henjj2 on 2019-10-18
Greetings.  I have a thinkpad T440 that I have been using ubuntu on for the past couple of years.  My machine has two hard drives.  A 16gb SSD and a 1Tb HDD.  I currently have the operating system on the SSD and my home directory on the HDD.  I ran into a problem the other day when I tried to install a flight simulator program and ran out of room on the SSD.  APT got stuck and I had to manually delete a bunch of other programs to get things running again.  My question is, If I re-install the operating system on the HDD what would be a good use of the SSD on this machine?  Thanks.

---

### Post by Impavidus on 2019-10-18
The best way to do this, I think, is to install the OS on the SSD, but the data files of the flight simulator on the HDD. What flight simlator is it? If you can find out where it stores its data (/usr/share/games/ maybe?), you may be able to create a separate partition on your HDD and mount it such that the flight sim data end up there.

---

