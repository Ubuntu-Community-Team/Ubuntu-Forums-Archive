---
title: "GRUB issues xp/kubuntu dual boot"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by zsirhc on 2008-08-14
GRUB issues xp/kubuntu dual boot
hey guys,

so i have 1 hard drive, 3 partitions
1.vista
2.xp
3.vista recovery that came with laptop

i erased vista partition split it in 2 and put kubuntu on it.

the problem is that grub did not detect xp it just picked up the recovery partition.
i assume this is becuz kubuntu wrote over the xp boot files.
i read i should try fixboot off the xp cd. no luck
i've been trying different things ive read online. but nothin seems to work.

I will post my fdisk -l and menu.lst
thanks for the help

sirhc

menu.lst (i skipped the stuff on top)
=======================================
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0e506ca6-9266-46bc-a219-aa2596f90e9b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0e506ca6-9266-46bc-a219-aa2596f90e9b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Windows XP
root		(hd0,4)	
savedefault
makeactive
chainloader	+1
===============================================

fdisk
==========================
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ae1ea1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       13778   110671753+   f  W95 Ext'd (LBA)
/dev/sda3   *       13779       14593     6546487+   7  HPFS/NTFS
/dev/sda5            2433       13778    91136713+   7  HPFS/NTFS
/dev/sda6               1        2310    18554980+  83  Linux
/dev/sda7            2311        2432      979933+  82  Linux swap / Solaris
=======================================
sda 5 should be xp
sda 6+7 are kubuntu
sda 3 should be the vista recovery
and to be honest i dont know what sda2 is.

thanks for the help

---

### Post by logos34 on 2008-08-14
sda2 is what's called an **extended** partition.  It's just a shell containing all your partitions except sda3.  

Try booting XP from the 'root (hd0,2)'--the recovery (notice the boot flag '*').  Maybe the boot files are there.  You cannot boot XP on a logical partition unless the boot files are located on a primary (either another windows installation or a dedicated primary boot partition).  If that doesn't work, it means the boot files were on the vista partition you deleted.  Backup and reinstall XP or do a repair reinstall.  (Obviously in ether case you'll need to restore grub afterward--see link my signature).

good luck

---

### Post by zsirhc on 2008-08-14
ok i tired (hd0,2) and i get 
starting up...
NTLDR is missing
ctrl+alt+del to restart.

i dont know what NTLDR is so i'll look it up till i get a reply.

thanks
sirhc

---

### Post by logos34 on 2008-08-14
actually you're going to have to reinstall XP to a primary partition (which means shrinking the extended down to make room).  I'm not sure whether or not the recovery partition can help you

---

### Post by Bobkins on 2008-08-14
You're sure doing fine, old cock

---

### Post by zsirhc on 2008-08-14
"actually you're going to have to reinstall XP to a primary partition (which means shrinking the extended down to make room). I'm not sure whether or not the recovery partition can help you"

ok i've seen the primary partition option when i was installing kubuntu. but im not sure what you mean with shrinking the extended down to make room.
So if your saying i need to reinstall windows then i'm going to delete the xp partition, or what i thought was the xp partition and choose that primary option when i make it a new partition. then reinstall xp on it.

i'll wait till someone responds before i do it.

sirhc

---

### Post by logos34 on 2008-08-14
> **zsirhc said:**
> 
ok i've seen the primary partition option when i was installing kubuntu. but im not sure what you mean with shrinking the extended down to make room.
So if your saying i need to reinstall windows then i'm going to delete the xp partition, or what i thought was the xp partition and choose that primary option when i make it a new partition. then reinstall xp on it.

you want to use Gparted from the ubuntu live cd to delete the xp partition and then shrink the extended to free up the space.  As you can see, sda5 goes from 2433 to the very end of the extended partition, 13778. After you resize sda2 create a new, primary ntfs in the space between the extended and sda3, the recovery.  Or else just leave it blank and let xp installer format it.

---

### Post by zsirhc on 2008-08-14
thanks for being more detailed.
i'll respond after i try all that stuff.
sirhc

---

### Post by zsirhc on 2008-08-31
its taken me forever to work on this laptop again but heres what happened.

when i try to delete the xp partition with gparted it says that i need to unmount any partitions with a label higher than 5.
Im not to sure what that means. but i decided to try the partitioner that pops up when you install ubuntu to delete it and try to go from there. that didnt work.


i downloaded partition magic, but just now as i'm typing this i realize that that isnt going to work becuz its probably for windows.

thanks for the help,
chris

---

### Post by caljohnsmith on 2008-08-31
> **zsirhc said:**
> its taken me forever to work on this laptop again but heres what happened.

when i try to delete the xp partition with gparted it says that i need to unmount any partitions with a label higher than 5.
Im not to sure what that means. but i decided to try the partitioner that pops up when you install ubuntu to delete it and try to go from there. that didnt work.


i downloaded partition magic, but just now as i'm typing this i realize that that isnt going to work becuz its probably for windows.

thanks for the help,
chris
Chris, do you still have your Windows logical partition? Because if you haven't deleted it, it actually is possible to boot Windows in a logical partition without too much trouble. See the great guide that meierfra put together about [booting Windows from a logical partition.]("http://ubuntuforums.org/showthread.php?t=813628")

If you need specific help with any of it, let me know.

---

### Post by zsirhc on 2008-08-31
yeah xp is still intact.
i'll read that guide and try it out.

i'll post back after that.
thanks.

---

### Post by zsirhc on 2008-08-31
I started reading over that guide. and this is step 3.

Step 3) Edit "boot.ini". The number in ``partition(1)'' needs to be changed to the correct number for your XP partition. Windows starts counting at 1 and counts partitions in the order of the partition table (so far that's the same way linux counts) BUT skips over extended partitions and empty partitions.

If windows skips over extended partitions when its counting, doesn't that mean it would skip over my xp partition because it is in the extended partition?

---

### Post by caljohnsmith on 2008-08-31
The way it works is Windows skips over the extended partition only, but still counts the logical partitions within that extended partition. So since sda2 is an extended partition, that doesn't count, but sda3, sda5, sda6, and sda7 do. And since your Windows seems to be on sda5, that would be considered "partition(2)" in that boot.ini file.

---

### Post by zsirhc on 2008-08-31
alright, i'll keep on with it then, just didnt wanna keep going for nothing

---

### Post by zsirhc on 2008-08-31
ok here are the two problems ive come across.

Step 3 Edit boot.ini

Code:

sudo nano /Win/boot.ini      (you may use a different editor than nano)

Change all "partition(?)" to "partition(3)" (there are two of them) Do not change anything else. Here "3" must be replaced by the correct number for you XP partition. See this post for some examples.



i dont know why they changed it to "3" in the example. 
========================================================
Step 4 Edit menu.lst:

Code:

gksudo gedit /boot/grub/menu.lst

Use

title XP
rootnoverify (hd0,4)
chainloader +1


Do NOT use "makeactive".
Of course (hd0,4) needs to be adjusted. The first number is the hard drive and the second number the partition. Grubs starts counting at zero, and counts the hard drives according to the order in the bios. So the boot drive is always (hd0). The second number is always one less than the number in the device name. So if Windows is /dev/sda5, then the second number is 4.
The "hd" is always "hd", even if the device name contains "sd".
If Windows is not on the boot drive, you need to add "map" lines:

title XP
rootnoverify (hd3,4)
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1



i think i need to add map lines and i dont know why they added them how they did, or how to add them for my situation.


i think i might have to perform step 5 but i'm not sure. id like to figure out the first two problems before continuing.

thanks,
chris

---

### Post by caljohnsmith on 2008-09-01
> **zsirhc said:**
> ok here are the two problems ive come across.

Step 3 Edit boot.ini

Code:

sudo nano /Win/boot.ini      (you may use a different editor than nano)

Change all "partition(?)" to "partition(3)" (there are two of them) Do not change anything else. Here "3" must be replaced by the correct number for you XP partition. See this post for some examples.



i dont know why they changed it to "3" in the example. 

The "3" was just for that specific example Meierfra gave, but bottom line is that your "boot.ini" needs to look basically like:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)[COLOR="Red"]partition(2)[/COLOR]\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)[COLOR="Red"]partition(2)[/COLOR]\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
```
So the two instances of "partition(X)" is the critical part; it needs to be "2" for you (as shown above) and not "3". 
> **zsirhc said:**
> 
Step 4 Edit menu.lst:

Code:

gksudo gedit /boot/grub/menu.lst

Use

title XP
rootnoverify (hd0,4)
chainloader +1


Do NOT use "makeactive".
Of course (hd0,4) needs to be adjusted. The first number is the hard drive and the second number the partition. Grubs starts counting at zero, and counts the hard drives according to the order in the bios. So the boot drive is always (hd0). The second number is always one less than the number in the device name. So if Windows is /dev/sda5, then the second number is 4.
The "hd" is always "hd", even if the device name contains "sd".
If Windows is not on the boot drive, you need to add "map" lines:

title XP
rootnoverify (hd3,4)
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1

i think i need to add map lines and i dont know why they added them how they did, or how to add them for my situation.


i think i might have to perform step 5 but i'm not sure. id like to figure out the first two problems before continuing.

thanks,
chris
Since your Windows XP is on sda5, that's (hd0,4) in Grub's world (just like Meierfra's example). So you should use the following in your menu.lst:
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1
```
Note you don't need any mapping lines, because your Windows is on the same HDD that Grub boots from. 

About step 5, you only need to do that if doing all the above steps doesn't make your Windows bootable; that's because most likely your Window's boot sector is just fine, but Meierfra included that for completeness in case that is a problem. 

Anyway, let us know how it goes and if you run into any more problems.

---

### Post by zsirhc on 2008-09-01
I got it working.
I left it as root (hd0,4),
when i changed it to rootnoverify (hd0,4) it worked.

thanks for all the help.
i learned a bunch of stuff doing this.

-thanks again
chris

---

