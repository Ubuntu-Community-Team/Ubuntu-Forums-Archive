---
title: "Trouble booting from usb hdd"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by krayziereysta on 2008-02-20
Well im a total newbie to ubuntu and well i decided to try it out after reading alot about it. well i wanted to install and boot it from my usb hdd because i didnt want to mess with my cpus main hdd. now i was able to install it (i didnt install GRUB because the first time i ever messed with installing Ubuntu, i had to reset the MBR because GRUB ran from the USB HDD rather than on the internal hdd). so when i rebooted, i set the BIOS to load from the USB HDD but then it said "Error loading operating system" so i dont know what i did wrong. do i have to install GRUB? and if i do, is there a way to install it to the internal hdd so i wont need the USB hdd connected always.

but perferably, is there anyway i could boot Ubuntu from my USB HDD whenever i have it plugged in and if i dont, the CPU loads XP as if there was no other OS? thanks in advance!

---

### Post by amohanty on 2008-02-20
Download and burn the desktop install CD, it is a Live CD [http://en.wikipedia.org/wiki/Live_cd](http://en.wikipedia.org/wiki/Live_cd) It does not install by default simply boots up and loads the OS from the CD and you can play around with it to accustom yourself to it.

HTH
AM

---

### Post by lbelmond on 2008-02-21
> **krayziereysta said:**
> 
1 - ...do i have to install GRUB? 
2 - and if i do, is there a way to install it to the internal hdd so i wont need the USB hdd connected always.
3 - but perferably, is there anyway i could boot Ubuntu from my USB HDD whenever i have it plugged in and if i dont, the CPU loads XP as if there was no other OS? thanks in advance!

Hello, 
I am a newcomer too, in the ubuntu (oh lets say "gnu/linux", and, accidentally, "ubuntu distro", because is perhaps the best, after having considered pro & cons, so if "gnu is not unix", then "linux is not only ubuntu", see ) world...
I'm having more or less your same doubts and problems... 
your three question make perfect sense, and are nowhere explained... unbelievable... along all this time anyone had similar questions? hum... very doubtful...
Anyway, I refused to install grub on hda0 (obviously, as you can see), and I got "MBR error 1", "MBR error 2", "MBR error 3" at startup... after three installations...
maybe someone of the guru should decide to write a little guide for all those people like us...
I will try again... stay tuned... If I will find something useful I will post it here...

---

### Post by Sweatbandman on 2008-02-21
I would also like to know! Especially on the whole load up the original OS (Vista for me) if the External isn't plugged in! :)

---

### Post by froy02 on 2008-02-21
To install Ubuntu on an external hard drive:
1. Use the Alternate Cd install disk.
2. When you get to the part where to install Ubuntu it write down the name of the drive you selected e.g. /dev/sdx or (hdx) where x is a letter for sd and x is a number for hd. 
3. When you get to the step where it ask you where to install grub tell it to install it to to the MBR of the drive that you wrote down in step 2.  Make sure that you specify a DRIVES like [COLOR="Red"]/dev/sda[/COLOR] or [COLOR="Red"]dev/sdb or (hd0) or (hd1[/COLOR]) BUT NOT [COLOR="Navy"]/dev/sda1 or /dev/sdb1 NOR (hd0,0) or (hd1,0).[/COLOR]
     Note: [COLOR="Red"]/dev/sda, /dev/sdb[/COLOR] are drives while [COLOR="Blue"]/dev/sda1 and /dev/sdb1[/COLOR] are partitions.  Like I mentioned before, specify a drive because grub can be installed in the MBR or the the partition.  You need to install it in the MBR of the USB drive. 
4. Now when you boot you select which drive you want to boot from by pressing the key for that choice (in my toshiba laptop it is 'F8') .  If you do not press any key or you do not have your USB drive connected it would boot up with your internal drive, Window$.

If you want to dual boot later you can use windows multi-boot option but that would be beyond this [COLOR="Blue"]Ubuntu forum.    
[/COLOR]
Hope this helps.

---

### Post by dstew on 2008-02-21
You have to install grub on that external hard drive in order for it to boot. To install it, boot a Live CD, open a terminal window and type```
grub
```That gets you the grub command line, with the grub> prompt. Of course, your external disk drive should be plugged in before you boot the Live Cd so it can be detected. At the grub prompt, enter```
find /boot/grub/stage2
```Whatever value it returns, use as the argument for the next root command.```
root (hd1,0)
```Use the grub disk number (the first part of the (hd1,0) value) as the argument for the setup command, to put the grub stage1 boot loader into the MBR of the external disk:```
setup (hd1)
quit
```Exit the Live CD system, remove the CD and reboot. You may have to tell the BIOS to boot the external drive.

One problem you can run into is if the BIOS changes the disk enumeration when it changes the boot order. In that case you might get a grub error when you try to reboot.
EDIT: You don't have to install the whole Ubuntu system again if it is already on the external drive.

---

### Post by lbelmond on 2008-02-21
=^.^=

---

### Post by Sweatbandman on 2008-02-22
Thats great thanks :)

Just a Few questions! When you say alternate CD do you mean the Live CD of the alternate version rather than desktop?

Also does it matter that the USB drive is FAT32?

Sorry for the questions!

---

### Post by dstew on 2008-02-22
> When you say alternate CD do you mean the Live CD of the alternate version rather than desktop?The Live CD and the Alternate Install CD install the same Ubuntu Desktop operating system. However, the Live CD lets you play with a temporary desktop first (if it works!). There is no "alternate version" of Ubuntu. Maybe you are thinking of the server edition of Ubuntu. That is a base system that does not have a desktop interface, and only uses the command line. I think that both the Live CD and the Alternate Install CD will allow you to install the server version if that is what you want, but I recommend installing the Ubuntu Desktop.> Also does it matter that the USB drive is FAT32?You should format the drive as ext3 when you install Ubuntu. I do not think Linux systems can be installed on a FAT32 file system. But, the installer will let you partition and format the drive in a way that is appropriate to Linux.

---

### Post by lbelmond on 2008-02-22
=^.^=

---

