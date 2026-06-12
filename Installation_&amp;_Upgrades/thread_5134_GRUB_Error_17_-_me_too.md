---
title: "GRUB Error 17 - me too"
date: 2004-11-15
forum: Installation &amp; Upgrades
---

### Post by wallysmyhero on 2004-11-15
I tried to load Urbuntu on my Win2000 pc in its own partition but when it boots up I get the above error.

I've read some of the other posts on this but don't really know how to proceed.

Is there some sort of GRUB 'uninstall' I can run so the system doesn't use it?  I can see the GRUB files on the partition if I boot from the cd but I cannot edit them because I'm not the owner.

HELP!!

---

### Post by dataw0lf on 2004-11-16
GRUB Error 17 indicates that it can see the partition, but it can't recognize the filesystem type.  Perhaps your root(x,y) settings are incorrect?
dataw0lf

---

### Post by wallysmyhero on 2004-11-17
Well...
My machine is toast.  MBR corrupted. Thank you Ubuntu for the opportunity to revisit the Windows installation programs.

Why should I ever try Linix again?

---

### Post by nEUrOO on 2004-11-17
maybe you only have to install lilo with your actual configuration
as lilo is not as "smart" as grub ... it would run throw the type of partition

---

### Post by rolf on 2004-11-17
Wally, maybe the warty live cd is for you (just a guess, but [http://releases.ubuntu.com/warty/warty-release-install-i386.iso](http://releases.ubuntu.com/warty/warty-release-install-i386.iso) is probably the one you want).

A live cd lets you boot from a cd and run (in this case) ubuntu - sort of a test drive, if you will.  It will not modify your hard drive contents in any way, shape, or form - a chance to run ubuntu without installing it.

---

### Post by FLeiXiuS on 2004-11-17
[QUOTE=wallysmyhero]Well...
My machine is toast.  MBR corrupted. Thank you Ubuntu for the opportunity to revisit the Windows installation programs.

Why should I ever try Linix again?[/QUOTE]


You shouldn't of gone that far with re-installing windows XP.  There's always methods to fix your solution, and this problem is perhaps very easy!

---

### Post by wallijonn on 2004-11-20
You may need to go into your BIOS and set the disk type to LBA (take it off AUTO. Windows, I believe, defaults to CHS even though it says "AUTO").

---

### Post by wallysmyhero on 2004-11-23
[QUOTE=FLeiXiuS]You shouldn't of gone that far with re-installing windows XP.  There's always methods to fix your solution, and this problem is perhaps very easy![/QUOTE]

Yea, perhaps.  I should have gone out a purchased a product like Norton's Ghost to back up the machine prior to letting the Urbuntu install touch it

But the real issue is you should not be 'allowed' to intall Urbuntu on an existing Windows machine in default mode unless you are replacing the windows OS.   You should only be able to do this in the 'Expert' installation mode.  This problem was identified (I checked in the Urbuntu bugzilla) prior to this thing being released but not corrected due to time constraints.

I wanted to try this product since it seemed to be a Linux flavor which could be intalled with a minimum of hassel.  Boy, I learned my lesson (btw - my machine was running win2k not xp).

---

### Post by Fireball007 on 2005-04-13
[QUOTE=FLeiXiuS]You shouldn't of gone that far with re-installing windows XP.  There's always methods to fix your solution, and this problem is perhaps very easy![/QUOTE]


Jep indeed if u reboot with your windows xp cd you can recover your MBR
Instead off installing windows choose the recoveryconsole and then type "fixmbr"
you'll get a warning but after that your mbr is fixed :)

---

### Post by gameman12 on 2007-02-16
i have like no experience in linux but plenty in windows, but, yeah, fireball's right, use xp disc to recover mbr.

safer bet

---

### Post by bulldog on 2007-02-16
Look at the date guys,it's a very old post,don't think he will give you any feedback :lolflag:

---

### Post by Scott Carlson on 2007-08-19
I have had this error 17 many times from having bad power downs and crashes for other reasons.  In most of my cases the problem is usually from a bad magic number in the root partition.  This can be easily fixed by doing this:
 
to fix error 17 in grub at boot time don't forget to try:

a. boot from any live CD (ubuntu install disk works for me)
b. open accessories->Terminal
c. in terminal type "sudo e2fsck -b 32768 /dev/hdaX

replace the hdaX in line above with the disk that you have your root mounted from
for example

sudo e2fsck -b 32768 /dev/hda2

in my case I have windows installed in /dev/hda1 and my root partition for ubuntu in at /dev/hda2
also if -b 32768 fails you can try other numbers including -b 8193 or -b 98304 or -b 163840....

The first time I had this problem it seemed I had to look for quite some time before the answer was found so I hope this helps most of you.  Good luck to you all and thanks for all of you that have made Ubuntu possible.

---

