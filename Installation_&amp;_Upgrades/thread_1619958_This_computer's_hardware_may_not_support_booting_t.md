---
title: "This computer's hardware may not support booting to disk"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by andreibraescu on 2010-11-12
Hi guys, 

I am a ubuntu user and I tried to install ubuntu on my sister's netbook too. The problem is that the netbook has a broadcom wi-fi n that is not supported by linux for now because I searched for drivers and other stuff an I found that it is not supported.
After that I tried to format the disk and reinstall windows 7 but the problem is that the installation procedure gives me this error: "windows cannot be installed on this disk. This computer's hardware may not support booting to this disk. Ensure that the disk's controller is enable in the computer's bios menu."

I tried to do all the things that are described here: [http://www.intilinux.com/howto/630/disinstallare-ubuntu-linux-e-ripristinare-lmbr-di-windows/](http://www.intilinux.com/howto/630/disinstallare-ubuntu-linux-e-ripristinare-lmbr-di-windows/) 
but it's still not working.

Obviously when I format the drive with ubuntu and I put it in the netbook it's not working, it stops at the logo and the only thing I can do is entering BIOS.

I formated the drive with a windows os and then the pc makes the boot from usb but the problem persit...I still can't install because of that error :"windows cannot be installed on this disk. This computer's hardware may  not support booting to this disk. Ensure that the disk's controller is  enable in the computer's bios menu."

Before installing ubuntu the sistem had kaspersky antivirus and detected 1 Trojan, it could be that a virus destroyed the bootsect...I don't think so...

Thank you for helping me :)

---

### Post by pricetech on 2010-11-12
first thing I'd try is resetting the BIOS to factory defaults.  I"d also check for a BIOS update.

---

### Post by oldfred on 2010-11-12
Some BIOS do have a way of locking the MBR, so you cannot install a virus into the MBR. Check BIOS settings.

---

### Post by andreibraescu on 2010-11-13
Hi guys,
 I fixed the problem!! :) :)
After formating and reformating and loading mbr on the hdd with ubuntu and with linux the things were not solved.
So I tried one simply thing, and everything went great! :)
 from the menu System/Administration/Disk Utility
I selected my hdd and and then in the bottom "Edit partition", I selected "BOOTABLE" and everything worked. 

Thanks guys ;)

---

### Post by pcxmac on 2012-02-18
Thanks for that tid bit, Ive been hitting this road block for about 7 hours and all I can say is I have done it before but now I know how it works.
 
What I did to dual boot with linux/Windows 7
 
 dont use the newer debian/etc installers, use fdisk in a linux console to partition the disk.
 like the poster above, ensure that the partition is marked bootable (assumed correct but not confirmed)
 boot up the windows installer and it will work !!!!
 
 btw, diskpart reallyl doesnt work very well, at least not for me, I followed a few microsoft site solutions/googled about it and it never worked out for me.
 
 I guess I will try to figure out the whole 'GPT' drives sooner or later, but 'fdisk' and what is currently supported by the more popular versions of grub works best for me at the moment.

---

### Post by uRock on 2012-02-18
Necromancy

Thread Closed

Please start a new thread for discussion of this topic.

---

