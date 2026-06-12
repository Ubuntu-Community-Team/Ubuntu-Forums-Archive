---
title: "Dual boot Vista/Ubuntu Hardy Heron"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by Renagade_Zerg on 2008-09-25
I have gotten my 2nd hard drive lately and I know this has been asked time and time again... but i cant boot vista. Ubuntu is on my first 150gig hdd while vista and my backup are on my 2nd 250gig hdd 
-----------------------------------------------------------------------
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10942    87891583+  83  Linux
/dev/sda2           10943       11185     1951897+  82  Linux swap / Solaris
/dev/sda3           11186       11307      979965   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000002fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12749   102400000    7  HPFS/NTFS
/dev/sdb2           12749       30402   141796352    7  HPFS/NTFS
---------------------------------------------------------------------
Vista is on the 100 gig partion /dev/sdb1. This is what I have in GRUB menu.lst
---------------------------------------------------------------------
title Microsoft Windows Vista
root (sd1,0)
savedefault
makeactive
chainloader +1
---------------------------------------------------------------------
any pointers would be very help full :)

---

### Post by caljohnsmith on 2008-09-25
Try using the following instead of (sd1,0):
```
title Microsoft Windows Vista
root [COLOR="Red"](hd1,0)[/COLOR]
savedefault
makeactive
chainloader +1
```
If that doesn't work, you may have to use Grub's mapping technique, but I've heard that Vista doesn't require it like Windows XP. Also, if that doesn't work, let me know if Ubuntu's entries use (hd0,X) or (hd1,X). Otherwise let me know how it goes.

---

### Post by Renagade_Zerg on 2008-09-25
Well it recognizes it but it seems the BOOTMGR, or boot manager I assume, is missing... should i just repair my vista install?

Edit: Sorry it took me so long I had class and didn't expect someone to answer so quickly

---

### Post by caljohnsmith on 2008-09-25
So when you try and boot Vista with that entry I gave, what exactly happens?

---

### Post by Renagade_Zerg on 2008-09-25
Starting up....

BOOTMGR is missing
press CTRL+ALT+DEL to restart...

---

### Post by Crafty Kisses on 2008-09-25
I'm not sure a boot flag will do the trick, but it is worth a try, boot Ubuntu via the LiveCD, open the Terminal and run the following:
```
sudo cfdisk /dev/sda
```
Select your Vista partition whatever it may be (/dev/sda3) and use the "boot" tab on the bottom to set a boot flag to the Vista partition. Next select /dev/sda* and use "boot" to remove the boot flag. Then use the "write" to save the settings. 

Like I said I'm not sure if a boot flag would make a difference, but it's worth a shot, please post back and tell me how it went.

---

### Post by Renagade_Zerg on 2008-09-25
Im using the LiveCD right now but my Vista partition is on my /dev/sdb1 partition so I used "sudo cfdisk /dev/sdb1" but is just gives me a fatal error
------------------------------------------------------------------------
FATAL ERROR: Bad primary partition 0: Partition ends after end-of-disk
                     Press any key to exit cfdisk
------------------------------------------------------------------------

---

### Post by caljohnsmith on 2008-09-25
Yes, I didn't notice before, but your fdisk output says:
```
Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, [COLOR="Red"]30401[/COLOR] cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000002fb

Device Boot Start End Blocks Id System
/dev/sdb1 1 12749 102400000 7 HPFS/NTFS
/dev/sdb2 12749 [COLOR="Red"]30402[/COLOR] 141796352 7 HPFS/NTFS
```
So your sdb2 ends on a cylinder greater than the total cylinders on your HDD; your HDD's partition table seems to be corrupt at this point. Do you know how it might have happened? When did Vista stop booting? What happened right before it stopped booting? 

You can use "testdisk" to try and repair your partition table, but before I give specific instructions to help you with that, it would be better if you can give me as much info as possible of what may have led up to these circumstances.

---

### Post by Renagade_Zerg on 2008-09-25
Well thats strange.... Vista booted fine up until I installed Ubuntu, I can try to boot Vista by unplugging my linux HDD but I really don't want to format that partition until its backed up it has TONS of my files on it <_< like music, movies, school work and stuff. If I can boot vista I'm sure I can back up my stuff onto the free space I kept on my linux HDD then resize and format that partition.

---

### Post by caljohnsmith on 2008-09-25
You shouldn't need to unplug your Ubuntu disk; can you go into BIOS and make the Vista drive first in the boot order? Or most modern BIOSes allow you to hit F12/F10 or something on start up so you can select which drive to boot on-the-fly.

---

### Post by Renagade_Zerg on 2008-09-25
Ya Ive had to do that before but you think its the corrupt tables thats causing it to not boot?

---

### Post by Renagade_Zerg on 2008-09-25
Well it seems my vista boot file was corrupt after the install but I fixed it via Vista installer disk so I think that's all that needs to be done. Ill get back to you after my next class <_< which strangely is a beginner linux class using Ubuntu. =D

---

### Post by Renagade_Zerg on 2008-09-30
It seems my Ubuntu install just eliminated my Vista booter <_< but changing (sd0,1) to (hd0,1) was the fix, although I had to repair my Vista install. I guess I assumed a SATA drive had to have a different command than an IDE <=3 silly meh but thank you guys very much

---

