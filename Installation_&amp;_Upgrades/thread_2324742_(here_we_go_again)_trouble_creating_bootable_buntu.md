---
title: "(here we go again) trouble creating bootable *buntu usb from win7"
date: 2016-05-16
forum: Installation &amp; Upgrades
---

### Post by antiOST on 2016-05-16
Hi

For the life of me, I cannot figure this one out. I'm moving from a kodi windows install to a ubuntu based. Thought it was a no-brainer but I cannot seems to create a bootable USB for this. 
I've installed lots of ubuntu way-back (6.*/7.*) so it not like I don't know how to choose usb as boot option.

I tried the following ISO images kodibuntu, xubuntu desktop, ubuntu server and none of the them boot. I tried making the bootable USB with Rufus, Universial USB installer and Unetbootin. NONE of them can make my usb boot! 

This works (but not what I need)!
I also tried downloading OpenElec and LibreElec packages (they are not ISO!) and used Rufus. I they just booted (and installed) without problem :confused:

What am I doing wrong, shouldn't I be able to make a bootable ubuntu usb in windows 7, just like that? 

Any help appreciated.

Kim

---

### Post by Bucky Ball on 2016-05-16
Yes, you should, just like that. ;)

Two things: what machine are you installing to and what version/flavour of Ubuntu are you trying to install.

Here's a suggestion for the *buntus. Use UNetbootin. Before you do, though, wipe the USB completely, create a new partition table if the Win software allows that (I wouldn't know) then create one FAT32 partition that takes up the whole USB dongle.

Where are you downloading the Ubuntu ISOs from? Are they checking out when your check the MD5SUM?

(Just a side note: we don't support Kodibuntu in this area but we can give you support attempting this with the others you mention. The Ubuntu Specialised Support areas are for questions regarding Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, Mythbuntu and Ubuntu Mate. ;))

---

### Post by antiOST on 2016-05-16
Thank for swift answer.

Checksums checks out!
As per your suggestion I tried to wipe, partition and format the USB** yes, it's possible in windows :)  
Then loaded the image in UNetbootin and onto the USB and boom it boots.... just like that!

I reckon that the total wipe and partition did the trick. Thank you!

** using DISKPART a command-line util for managing disk, volumes and partitions which is included as standard in windows

---

### Post by Bucky Ball on 2016-05-17
Fantastic! UNetbootin likes them completely cleaned and wiped and with a FAT32 partition before it want to play nice. :)

As your original issue is solved, could you please mark the thread as solved to help others using thread tools at the top right or follow the second link in my signature at the bottom of this post. Thanks, good luck and don't hesitate to post a new thread for any other questions/issues.

---

