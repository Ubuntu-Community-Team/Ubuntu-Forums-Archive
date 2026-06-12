---
title: "Dapper on external HDD?"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by nolongerlivecd on 2006-07-03
This was done using the instructions from [http://www.ubuntuforums.org/showthread.php?t=80811&page=42](http://www.ubuntuforums.org/showthread.php?t=80811&page=42)

I just installed on my external Hard Disk 40GB Seagate 2.5", using the Dapper pressed CD, the free ones ordered from ShipIt.

The install was smooth, but I did not monitor it, only a quick glance now and then.

I installed it on sda3, as my hard disk currently is:

Size mount type usage
5GB / ext3 Ubuntu
0.5GB /swap swap Swap
4.5GB ? FAT32 Programs
30GB ? FAT32 Data

I didn't see GRUB get installed, and I can't access rescue mode on either 6.06 or 5.10 live and install CDs.
I can't boot from the hard disk either, even though my motherboard is supposed to support it (Intel 865PERL).
What should I do?
nolongerlivecd is online now   	Edit/Delete Message

---

### Post by givré on 2006-07-03
Is your external disc an usb one.
If it is, try that : [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by nolongerlivecd on 2006-07-04
After reading that, I'm slightly confused. I thought DaBruGro's original mehtod did not involve a CD, and could boot directly from the HDD?

---

### Post by nolongerlivecd on 2006-07-05
Yeah, It's USB, and it did successfully boot, up till Mounting Root Filesystem. It was lagging here, so I unplugged and plugged it back in. However, there was no ok in the other column, and it was stuck at Waiting for Root Filesystem... From there, it took 2 minutes before I realised that it wasn't going to work. I repeated the plug/unplug, and now, it still is stuck.

Maybe DaBruGro could customise the kernels as packages for "linux-686-usb"?

---

### Post by nolongerlivecd on 2006-07-05
It works now, on a different computer. Updated, installed the kernels... then suddenly, the top panel's apps launcher disappeared! (I mean the Applications, Places, System thing)

Can anybody teach me how to restore it? The rest are still there.

---

