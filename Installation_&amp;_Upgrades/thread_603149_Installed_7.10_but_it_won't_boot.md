---
title: "Installed 7.10 but it won't boot"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by singlewc on 2007-11-04
Neither will 6.1 when I tried to install it months ago....

I ran the live CD, looks nice. It won't install as qparted throws up and hangs me out to dry,just as it did with 6.10. Back then, the advice was to get the alternate CD to install, and back then I did, and I got the exact same problem then, as I did tonight.

Using the 7.10 alternate CD, the install went flawlessly,put Grub in MBR, rebooted, and it runs through the checks, and pukes when it tries to fsck sda5 (why is it sda5, when its an ide drive, and all other linuxes call it hda5?)

Anyway, it just hangs there for as long as I want to wait. Half an hour this last time. 

I am tired of wasting my time trying to install ubuntu. I want to get in there, and have some fun. Its about the tenth time I have tried to install this distro. I'm pretty sure its the last time, so I hope someone can help me out

This is what is on the screen. Had to write it, and type it up, so excuse any typos.

---------
Checking root file system
fsck 1.40.2 12 jul 2007
dosfsck 2.11 12 mar 2005, fat32, lfn
There are differences between boot sector and its backup
Differences  offset: original/backup
28:3f/c5  29:00/ed  30:00/3b, 31:00/01
Not automatically fixing this
/dev/sda5  22863, 585706/1280052 sector

............................................

---------------

and here it sits forever and ever and ever

sda1 is an ntfs partition with windows2K on it.

sda5 is the first fat32 data partition
there is an sda6 that is also fat32

did checkdisk repeatedly from windows, and from a bootable CD so I know sda5 is clean.

If I am gonna use ubuntu, I have to be able to boot it up.

Any help? Please?

John

---

