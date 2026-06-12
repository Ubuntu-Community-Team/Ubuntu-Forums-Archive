---
title: "Grub Error?"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by bryanismynamo123 on 2010-01-11
Okay, well I recently had an 80gb hdd and I had XP on it, with 30 gigs, I tried to move the other 50gigs and it didnt work so I installted Ubuntu. I tried to rearange the partition size by going back into the installation setup. Didnt work, so I went back into windows and deleted the ubuntuu partion. Bad idea. :(
 
Now when I boot my computer it says:
GRUB Loading.
error: no such partition
grub rescue>
 
Any tips? Is the computer dead? I messed it up so many times! 
 
Thanks in advance. :KS

---

### Post by puzzler995 on 2010-01-11
I can tell you its not dead

---

### Post by bryanismynamo123 on 2010-01-11
Then why is it not working?

---

### Post by vinnywright on 2010-01-11
grub frome ubuntu is still trying to be your boot loader but you have deleted it's config files that were in /boot/grub in ubunto so it dosent know what to do.

if you have your XPcd boot it into recovery console and run fixboot and fixmbr

VINNY

---

### Post by bryanismynamo123 on 2010-01-11
I changed all my boot thingies to boot from CD and it still doesnt boot from the XPcd

---

### Post by bryanismynamo123 on 2010-01-11
And what do you mean fixboot and fixmbr?

---

### Post by vinnywright on 2010-01-11
> **bryanismynamo123 said:**
> And what do you mean fixboot and fixmbr?

fixboot and fixmbr are 2 of sevrall comand's that can be run frome the recovery console on the xpcd.

to fix thing's ........look it up

O heck hear

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

VINNY

---

### Post by darkod on 2010-01-11
The procedure to restore XP bootloader, and others, is here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

But you have to be able to boot with the XP cd. You need to make sure CD is before HDD in your BIOS boot options, or if you have Quick Boot menu on your computer just use that and select to boot from cd.

---

### Post by vinnywright on 2010-01-11
> **darkod said:**
> The procedure to restore XP bootloader, and others, is here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

But you have to be able to boot with the XP cd. You need to make sure CD is before HDD in your BIOS boot options, or if you have Quick Boot menu on your computer just use that and select to boot from cd.

sweet bookmarking that one as I dont type so well and it get's asked a lot.............LOL

VINNY

---

### Post by puzzler995 on 2010-01-11
See I told you you would get help here :) These guys know more about Windows than Microsoft's tech support :D

---

### Post by presence1960 on 2010-01-11
An alternative way to fix your MBR to boot windows is boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
sudo apt-get install lilo
```

When that is completed then run ```
sudo lilo -M /dev/sda mbr
```
use sda if you only have one hard disk, otherwise substitute the designation of the disk that has windows on it- i.e. sdb, sdc, sdd, etc.

Reboot without the Live Cd and you will boot right to windows.

---

### Post by puzzler995 on 2010-01-12
> **presence1960 said:**
> An alternative way to fix your MBR to boot windows is boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
sudo apt-get install lilo
```

When that is completed then run ```
sudo lilo -M /dev/sda mbr
```
use sda if you only have one hard disk, otherwise substitute the designation of the disk that has windows on it- i.e. sdb, sdc, sdd, etc.

Reboot without the Live Cd and you will boot right to windows.

Lilo... Hate to say it, but that looks nicer than GRUB!!! :lolflag: Might have to get it for myself!!!

I kinda got the OP in this mess so I gotta help him, and since I kinda know what I'm doing better than he does, I'll take control of his computer, via RDC, and do that for him(I assume RDC works on a LiveCD...)

---

### Post by puzzler995 on 2010-01-12
thanks presence1960 it worked. I suspect my friend will be on soon to thank you also. :D

---

### Post by presence1960 on 2010-01-12
> **puzzler995 said:**
> thanks presence1960 it worked. I suspect my friend will be on soon to thank you also. :D

You are welcome. Glad it worked!

---

### Post by bryanismynamo123 on 2010-01-13
Thank you so much guys! The computer is working again!!
Thanks again!:KS

---

### Post by bryanismynamo123 on 2010-01-13
oh and especially thanks to you, presence1960!):P

---

