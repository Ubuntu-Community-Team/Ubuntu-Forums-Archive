---
title: "Cannot install, hard drive not recognized? Help."
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by bigred1978 on 2010-08-01
Hi there!

I am new to UBUNTU and I am trying to install this OS.  However no matter what I do the UBUNTU instllation CD doesn't recognize the hard drive on which I would like to install the OS on.

I currently have two SATA hard drives connected to my computer.  MY primary is my Windows 7 drive and my second hard drive is my spare.

When i load up UBUNTU and get to the window where I can select which hard drive/partition to install to my second spare drive isn't there...any ideas?

Help would be much appreciated, thanks!

:D

---

### Post by jmfal on 2010-08-02
Do what I did :unplug hdd with windows> install ubuntu on other hdd, make sure it`s running good> shut off pc> reconnect windows hdd> restart >boot menu> choose which os you wan`t, then you don`t have to mess with grub
 hope this helps you.

---

### Post by bigred1978 on 2010-08-02
Hi,

thanks for the advice.  I tried what you said but still no good.  This time around with only my spare drive connected nothing showed up, nothing at all.  I guess it something having to do with my motherboard and or hard drive.

:(

---

### Post by ronparent on 2010-08-02
The solution may be as simple as plugging in to another SATA port. Other factors possible: A drive previously used in a raid (the raid bios doesn't need to be engaged); a SATA2 drive plugged into a SATA3 port.

---

### Post by oldfred on 2010-08-02
IF you have RAID, Do NOT run this:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

I have also seen NTFS partitions that need chkdsk run before the drive is seen. I had that happen with my sda. Gparted would not see sda and took forever to see sdb & sdc. I thought it was just because I had a lot of partitions. After running chkdsk on my NTFS partition gparted comes right up.

---

