---
title: "Problem with grub and winXP on 2nd hard disk"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by jonboy99 on 2006-12-09
Am having a slight problem getting grub to let me load windows XP, when XP is on a second hard drive.
My setup is:
First hard drive - multiple partitions, with several linux versions, and win XP on the first partition.  Grub is on this drive.  Kubuntu dapper is my main OS and where the menu.lst file exists.

2nd hard drive - just one partition, all winXP (ie a second copy) - this is where I run my games from.

I have added the bottom entry to try and load the winXP on the second drive, but when I choose it from the bootup menu it just drops me to a grub prompt.  All other menu selections work fine.  Any ideas?  The bottom but one entry loads the copy of XP on the first drive just fine, so I thought i'd just the change the drive number from 0 to 1 and it should work?


Cheers
Jon

PS if I change the bios to boot directly from the second drive, the copy of windows XP on there boots just fine.

This is the bottom part of my menu.lst - I cropped off the rest as it's probably irrelevant and long.

```
# linux installation on /dev/hda5.
title		Ubuntu, kernel 2.6.12-9-386 (recovery mode) (on /dev/hda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda5 ro single 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda5.
title		Ubuntu, memtest86+ (on /dev/hda5)
root		(hd0,4)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

#Added by Jon 101206 for 160gig windows drive

title		Microsoft Windows XP Professional - gaming
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by bulldog on 2006-12-09
Add the map options to the entry of your second disk XP
```
#Added by Jon 101206 for 160gig windows drive

title		Microsoft Windows XP Professional - gaming
rootnoverify		(hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader	+1
```

Make your entry like this and it will boot fine.

---

### Post by jonboy99 on 2006-12-09
Works perfect - now that's community support! :D 

I'm vaguely remembering now that XP has to be on the first hard drive - I presume that's what the mapping does?

Cheers
Jon

---

