---
title: "Partition problems"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by Onwlyix on 2007-07-09
Long story short, in an attempt to install Ubuntu Linux, something messed up (Error message was something about Ubuntu not being able to recognise the partition ?) and now none of my partitions are working. When I try and boot from my hard drive, BIOS says "0 active partitions", and when I open the partition editor on my Ubuntu LiveCD it shows nothing but unallocated space. The weird thing is, I can still browse my files through Nautilus. My 160GB USB external hard drive, which was also shown to be unallocated space, is also visible in Ubuntu (both are read only) and works perfectly on my other computer (on XP). I tried doing a repair install with my XP Re-install CD, but it said my C: Drive was corrupted and setup could not continue. I then ran chkdsk /r and got this:
```

chkdsk has finished checking the volume
48949404 kilobytes total disk space
12820264 kilobytes are available

4096 bytes in each allocated unit
1223751 total allocation units on disk
3205066 allocation units are available on disk

```
After that I tried a repair install again. It did it's thing, restarted, and it still says 0 active partitions on boot. Any idea how to fix it and restore my windows part? Thanks.

-Tru7h

---

### Post by tetsura on 2007-07-09
Have u tried fixmbr in the xp recovery console from the disc? that should restore the mbr and hopefully you'd be able to boot into windows.

---

### Post by Pumalite on 2007-07-09
Try Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by Onwlyix on 2007-07-09
tetsura, I tried fixmbr and now when I boot it says "press f1 to retry boot, f2 for setup." I've looked over the settings and the boot order is right, but it's still not booting.

Pumalite, Gparted *is* the partition editor on the LiveCD.

---

### Post by tetsura on 2007-07-09
Have you tried right clicking the windows partition in gparted and ticking the box next to boot in 'manage flags'?

---

### Post by bren on 2007-07-09
it sounds like your partition table is messed up 

that happened to me at install time too and i fixed it much to my relief using testdisk utility

start this rescue CD (boot from it) then right click on the desktop and choose testdisk

when you start test disk you need to check / select the primary partion and that the types of partition are correct

it takes some moments to work out what testdisk options do but after a couple of minutes it is clear and it works!

hope it works for you

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) 





bren

---

### Post by Onwlyix on 2007-07-10
I'll post back tommorow after I get a blank CD to burn that to. It looks like it might really help. Thanks. :-D

tetsura, I can't. There's no partitions in Gparted, just a block of grey unallocated space. All the partitions are visible in Nautilus though, and fully readable (on Fiesty only, I'm using Dapper ATM because Fiesty has some trouble with my monitor)

---

### Post by tetsura on 2007-07-10
ah ok sorry, good luck :)

---

### Post by Onwlyix on 2007-07-11
Agh, I keep forgetting to get a CD. BTW, when I do, what can I use to burn the ISO from Ubuntu? I don't know of any image burning programs for linux.

---

### Post by Pumalite on 2007-07-11
k3b. Install through Synaptic. Go to Tools>Burn CD Image>Choose location of iso>Burn. (BTW,  Gparted the stand alone program that burns to a bootable CD is not exactly the gparted that comes with Ubuntu. In my experience is more secure, more flexible, gives you more options, you have more control of what you are doing and in general is better to use first, before install to prepare your drive)

---

### Post by Onwlyix on 2007-07-12
Okay, well I found and download the testdisk alone so I don't need to burn the iso or anything... Now, I have no idea how to use this, and after my second ordeal involving partitions, I'd like a little help before I dive into this. Could someone post some instructions or a walkthrough of the process so I don't re-write something that doesn't need to be re-written or some such error? 

Thanks! :)

---

### Post by bren on 2007-07-12
you may still need it on an iso

only when you are booting from CD does the OS have the power to change the properties of ALL the partitions.....

i don't know if you can run testdisk as you suggest - it might work if the info you need to change is not on or your partition where you boot from...

when you run it

(this from memory and a while ago)

first you have to choose which size your HD is - it should offer you two options - one which is clearly right, one which is clearly wrong

then hit OK or choose option to ANALYSE and it brings up the parition table

check the partitions are the right type (VFAT etc) and the primary partion is marked '*' to mean it is primary AND bootable (usually this is your win partition on a dual boot machine)
if not then you can manipulate by various keystrokes (see key at bottom of screen)

if all ok then hit ok a few times and exit

although it seems sometimes you didnt do anything (if partition info was correct on entry) still I think you will now find when you exit and boot gparted that all partitions now show data and boot to your other OS should work again....

that was my experience anyway...
so it must write partition table on exit i think...

good luck

bren

---

### Post by Onwlyix on 2007-07-15
I finally got around to running testdisk (I've been kinda busy). I hit Analyze and pulled up the partition table, and yay, I see my partitions! Here's both partition tables (the one right after hitting analyze and the one in green). Everything looks okay, but I'm not sure if Dell Utility needs to be bootable or not. I don't know if it was before. I'm pretty sure the NTFS part needs to be bootable, but I'm making sure before I jump into anything like I did last time to get into this mess.


```

     Partition                  Start        End    Size in sectors

 1 P Dell Utility                     0    1  1       5 254 63        96327
 2 P HPFS - NTFS                  6   0  1  6100 254 63   97916175
 3 P CP/M                       9288   0  1  9724 254 63     7020405
 4 E extended                 6101   0  1  9287 254 63   51199155
No partition is bootable

```

```

     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     5 254 63      96327 [DellUtility]
P HPFS - NTFS              6   0  1  6099 254 63   97900110
P Linux                 6101   0  1  9287 254 63   51199155
P FAT32 LBA             9288   0  1  9724 254 63    7020405 [DellRestore]

```

---

### Post by bren on 2007-07-15
>      Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  4255 254 63   68372577 [439013]
 2 P Linux                 4256   0  1  5530 254 63   20482875
 3 E extended LBA          5531   0  1  7060 254 63   24579450
 4 P FAT32 LBA             7061   0  1 12160 254 63   81931500 [DATA]
 5 L Linux                 5531   1  1  6805 254 63   20482812 [HOME]
   X extended              6806   0  1  7060 254 63    4096575
 6 L Linux Swap   
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted


Hi Onwylix

I checked and mine is as above - the NTFS is marked as primary bootable
I don't have Dell Utility on my machine but I would try making the NTFS one as per mine and see what happens....

You can always change back now you have test disk :-)

You may have to repair GRUB as well to get your multiboot back...

bren

---

### Post by Onwlyix on 2007-07-15
I'm about to reboot after writing the changes.... I hope It works! If it doesn't, I'll let you know. Same if it does. If I don't reply at all ubtil monday or tuesday, I messed something up. XD

---

### Post by Onwlyix on 2007-07-15
Joy! I have my windows back! Yay! I'll probably be back in a few weeks once the shock of losing and regaining windows and all my programs wears off. Dual boot FTW.

THANK YOU ALL SO MUCH!

Tetsura, Pumalite, and Bren! I would be stuck if y'all didn't help. Thank you thank you thank you! :D I appreciate all of your help!

---

### Post by bren on 2007-07-16
hi onwlyix

Great :-)   It feels nice to get you out of same hole I fell in :-)

By the way....

- if you search forums you will see that fail on install esp where there is hidden utility or restore partition does happen (occassionally)    other one that gets mentioned a lot is where end of boot partition crosses sector boundary (or something like that)
- i used alternate CD for install after std one quit during partition process and all went good - try that route or get an XP utility to free up space on partition before you start and am sure you will be ubuntuing happily....
- how do we get Ubuntu to include testdisk on the LIVECD!    It deserves it!

good luck

bren

---

