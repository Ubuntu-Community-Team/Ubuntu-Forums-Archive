---
title: "Moving from desktop to USB.  Is it this easy??"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by Deadheded on 2010-03-06
About 6 months ago I had to get a laptop for work.  It is great and I find myself spending about 90% of my computer time on it.  Because of the work I do in order to run certain proprietary company software I have the hard drive encrypted and pre-xp load security.  I can't even plug in a usb drive without encrypting it.  

But I can boot to a USB linux install as long as it does not touch the hard drive.  

I want to move my desk top to one of my USB pen drives.  I have already made several live USB loads so that is not a problem.  If I simply copy my /home folder to a live USB copy of Ubuntu and re-install a couple of programs I use should everything be usable and work?

Just looking for a little advice before I jump in...

TIA

---

### Post by jerrrys on 2010-03-06
if you wish to write to it, you need to do a persistent install.

---

### Post by Browser_ice on 2010-03-06
The easiest way to have a bootable and persistent USB keyed Linux (I have done it several times) is to install directly to the USB key instead of the Desktop's HD also install the grub on it so your PC is intact and so you can use your key just about on any PC. You will have to consider the followings :

1) where will you put your swap partition ?
--- on the PC will require creating a partition
--- on the USB key, it will work but again create a swap partition on it

2) the format of your USB key partitions: I recommand using ext2 as higher ext versions will create addition write cycles to your USB key and therefore, decrease the life of your USB key (you could as your USB key maker for how long your kill will live with a Linux on it, I did it and they said 5000 write cycles on my OCZ 8Gb key).

3) if you want to use your USB keyed Linux anywhere, then you will have to create bootable GRUBed floppy. Not all PCs have USB key recognition on boot and you might not even be able to change the bios to boot from a USB also.

One cool thing you can do with your USB key is make an ISO backup of it. Why ?  Because you never know when you will accidently break your key and also, because you can restore on it any Linux version you want (once you installed them and ISOed them).

---

