---
title: "Install on external hard drive"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by mgiavr01 on 2013-05-06
Hello,
I am new to ubuntu and i would like some help.
I have a laptop with windows 7 installed but i would love to have ubuntu too because it's a great OS.
So i would like to install ubuntu on an external usb hard drive (320 - 500 GB) and i have some questions about that :

 - Do i need a usb external hard drive which will be compatible with ubuntu - linux ? or i can do it with any hard drive 
 - If i make a partition on it for ubuntu staff will i be able to use it and save other staff in the usb hard drive (movies,songs,documents etc) ?
 - If i have ubuntu installed on the usb hard drive will i be able to boot ubuntu from any pc ?
 - Are my changes going to be saved normally or my settings will be lost after shut down ?

Waiting for your answers, if something is not explain well tell me to try explain it better .
Thank you!

---

### Post by pfeiffep on 2013-05-06
I am answering this using a Linux Mint installation on an external USB2 hard drive.:KS

> [COLOR=#000000]- Do i need a usb external hard drive which will be compatible with ubuntu - linux ? or i can do it with any hard drive [/COLOR]
Probably any hard drive will work, You need to insure that your PC will boot from USB
> [COLOR=#000000]- If i make a partition on it for ubuntu staff will i be able to use it and save other staff in the usb hard drive (movies,songs,documents etc) ?[/COLOR]
You will need to use 'something else' when installing as an option to insure the flexibility of saving space for data. If the goal is to share the data with other OSes consider if you need Windows to access data. Newer Windows can read read NTFS partitions, but not ext#. 
> [COLOR=#000000]- If i have ubuntu installed on the usb hard drive will i be able to boot ubuntu from any pc ?[/COLOR]
If the goal is transportablity then you should probably choose a 32 bit version rather than 64. I also suggest USB2 rather than 3 will provide greater acceptance among different PCs. Some PC's cannot boot USB. When installing remember that Linux drives are identified as /dev/sda, /dev/sdb, and so on. If you have only 1 internal drive and 1 external drive you'll want to choose /dev/sdb to load grub2. Newer PC that boot with [UEFI]("http://www.uefi.org/about/") will prove somewhat problematic
> [COLOR=#000000]- Are my changes going to be saved normally or my settings will be lost after shut down ?[/COLOR]
If you truly install (vs making a live dvd type installation) your OS will be very similar to one installed on an internal HD. This[ post]("http://ubuntuforums.org/showthread.php?t=2130569") might help

---

### Post by C.S.Cameron on 2013-05-06
Format the hard drive NTFS, then use "Something else" for partitioning , leave the first partition NTFS for use transferring files to/from Windows computers, format the second partition ext4 and use for "/", make the third partition swap so the computer can hibernate.

---

### Post by mgiavr01 on 2013-05-08
Thank you for your answers, i discovered that my laptop can't boot from usb so there is nothing else to discuss! 
Tell me if i am wrong ... but i figured out that it can't boot from usb when i opened BIOS and tried to change the "where to boot from" order i had only three options
1. CD/DVD
2. my hard disk
3. Network : Realtek boot agent

That meens that i can't boot from usb right ?

---

### Post by fantab on 2013-05-08
No, that does not sound right. There will be an option in BIOS to "enable/disable" USB Boot. Since you are using laptop which presumably came pre-insalled with Win7.. it has to have that option. Enter your BIOS setup and Check again. I use a Vista time BIOS and it not only has the option to enable/disable USB boot, it also has the option of 'booting usb devices first'.

---

### Post by oldfred on 2013-05-08
Both my laptop & desktop from 2006 had BIOS that booted from USB. May be BIOS setting as above, on my laptop it only appears in list if Flash drive is inserted and bootable when booting. On desktop I have many USB default boot options, but none of them boot my flash drives. Flash drive appears as another hard drive and I have to click on hard drive to boot and it opens another window with choice of hard drive and it shows USB flash drive.
I do not use external hard drive but all my flash drives are seen the same as external drives.

---

### Post by C.S.Cameron on 2013-05-08
Check out Plop Boot Manager, It can give older computers the ability to boot from flash drive or other USB.

Perhaps you only need to set your USB as first hard drive in BIOS to boot from it.

---

### Post by Lightning Dragon on 2013-05-08
Hi,

> So i would like to install ubuntu on an external usb hard drive (320 - 500 GB) and i have some questions about that:

- Do i need a usb external hard drive which will be compatible with ubuntu - linux ? or i can do it with any hard drive 
 - If i make a partition on it for ubuntu staff will i be able to use it  and save other staff in the usb hard drive (movies,songs,documents etc)  ?
 - If i have ubuntu installed on the usb hard drive will i be able to boot ubuntu from any pc ?
 - Are my changes going to be saved normally or my settings will be lost after shut down ?


No. Some USBs do not work. I have found various Sandisks to not work. So it depends on your USB brand. What is it? I have tested Toshiba and Sony USB drives to be working, so if you have those I think you are golden.
I'm not sure what you mean. Will it work like a regular install? Then yes, only it will be on a USB.
It would depend on the computer really.
If you follow pfeiffep's replies, then no, you can set it up to work like a normal install.

Now I must ask you what your computer is. I thought mine could not boot USB because it wasn't in the BIOS, but it can. For me I had to press "ESC" at power on and it took me to an entirely different menu called "Boot Menu", where I was given a blue box with all my options to select from. For me it listed my USB there not as "USB" but as the brandname and name of the label it had, which was "TransMemory Toshiba". For you it will be different, but it will be there. If you have HDDs hooked up, external or internal, unplug them so you can see only your disk drive and USB in the listing.

I also did this with my Acer One laptops and a larger laptop that did not list "USB" in the BIOS.

---

### Post by mgiavr01 on 2013-05-09
Ok , i checked better and when i had connected the usb there was a 4th option which was the usb.
Thank you all for your answers :)

---

