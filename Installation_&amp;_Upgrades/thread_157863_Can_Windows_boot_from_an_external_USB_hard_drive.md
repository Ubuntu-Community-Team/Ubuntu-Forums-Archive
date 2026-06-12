---
title: "Can Windows boot from an external USB hard drive?"
date: 2006-04-10
forum: Installation &amp; Upgrades
---

### Post by slag on 2006-04-10
I love my Ubuntu setup, but I just got a new external USB hard drive for my birthday.  I would like to use a bit of the extra space to set up a Windows installation for gaming.

Unfortunately, the windows setup disc didn't like me trying to install windows to the USB partition.  It has something to do with loading drivers (or maybe just that Windows sucks.)

Here's my current scheme:
Laptop - 60GB internal, Kubuntu 5.10
External - 60GB NTFS partition for Windows
External - 100GB FAT32 partition for media storage

Any suggestions/ideas?  I guess I could reformat everything and put Windows on my internal hard drive instead of Linux, but I'd hate to think that when I'm on the go I'd have to use Windows instead of Linux (I won't ALWAYS be able to have my external hard drive with me...)

I hate Microsoft.  Let me do what I want to!  I paid for this garbage!

---

### Post by anders.ostling on 2006-04-10
Yes you can install windows on an external disk. However, it is wasted time since the booting will fail when the XP kernel resets the usb bus halfway into the boot ... basically committing harakiri ... mayby in a future service pack, or Vista. 

The trick to install on an external usb disk is to disconnect (physically) the internal harddrive before booting the CD installation disk. After the installation is ready, you can re-connect the internal drive. However, the usb reset thing will still not let you boot all the way into XP. It's not a bug but by design. 

Anders

PS. Note that I am talking about plain XP. I think there is something called PE boot that can be used with Xp for mobile devices and usb disks. Google is your friend.

---

### Post by slag on 2006-04-10
I decided to do the following:

internal: 30GB ubuntu, 30GB windows
external: 160GB fat32 media storage

---

