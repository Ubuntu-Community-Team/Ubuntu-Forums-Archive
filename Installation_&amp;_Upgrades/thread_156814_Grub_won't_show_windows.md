---
title: "Grub won't show windows"
date: 2006-04-07
forum: Installation &amp; Upgrades
---

### Post by heinzbitte on 2006-04-07
Sorry about first post being help and all.

      I have two harddrive.  One is partitioned to 100gigs which is fat32 with all my media so I can share with linux and windows.  The other 20 gig partition I just installed windows on and it worked fine, and I would really like not to have to reinstall it yet again.  The other hard drive is 15 gigs and just has Ubuntu 64 bit installed on it.  

     So here is my problem.  Windows boots up fine.  I install Linux and everything seems to be working fine.  It starts up and everything is good.  I then decide to go into windows.  So I restart and go into the Grub boot loader, windows isn't there.  There are like 6(3 with its other like copy or whatever) versions of ubuntu and the memtest.
 
    I tried taking out the 15 gig harddrive and just starting from the other harddrive but it tells me something about something failing and insert a system install disk.


I don't quite know what to do know.  Can I change Grub to have it somehow?

Also, I checked with linux and the partition is still there with NTFS file system so it seems like it wasn't destroyed or anything.

I just don't want to install windows again but want it working.

Thanks and sorry and all that junk.

EDIT: The 15 gig with linux is hda1
The one with windows installed is sda5
and the vfat/fat32 one is sda2

I didn't find a thread like this when I searched but I found one like this after posting this so sorry if this was answered.  But do I need to change where the windows partition is or something?

---

### Post by Herman on 2006-04-08
Hello, heinzbitte,
One idea is to try experimenting with the Grub command line (press 'c' from the grub menu) and type something like these commands:
```
grub > root (hd0,1)
grub > map (hd0) (hd1)
grub > map (hd1) (hd0)
grub > makeactive
grub > chainloader +1
grub > boot
``` If those don't do any good, try replacing (hd0,1) with (hd0,0) and leave out the two 'map' commands. Also try replacing 'makeactive' with 'savedefault' too maybe, and try replacing 'root' with 'rootnoverify'until you find some combination  that gets Windows to boot.
When you find out which commands make Windows boot up, write it down and add that to your /boot/grub/menu.lst later on. If you know how you can also add it by pressing 'e' (for edit) from the grub menu. More info [here]("http://www.users.bigpond.net.au/hermanzone/p15.htm").

I notice you have Windows on sda5, that partition number (5) indicates a 'logical' partition. It is more common to install Windows on a Primary partition, but as long as it will boot for you I guess it's okay on a logical one.

A second way to get Windows to boot is to try out [GAG Boot Manager]("http://gag.sourceforge.net/"), you can run that from a CD, floppy disk or install to a hard drive. I have a how-to for that [here.]("http://www.users.bigpond.net.au/hermanzone/p12.htm")

Good luck with it, I hope I am being helpful, Regards, Herman :D

---

### Post by heinzbitte on 2006-04-08
Thanks Herman,  I will try that now.

Edit I couldn't quite figure out what to do.
Can I edit it in /boot/grub/menu.lst that file somehow, so I can have more chance of knowing what to do?  Also that doesn't even have windows XP on it it says 
```
title		Ubuntu, kernel 2.6.12-9-amd64-generic Default 
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Default (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/hdb1 ro single
initrd		/boot/initrd.img
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
```
Can I add windows from there?
```
heinzbitte@ubuntu:~$ cat /boot/grub/device.map
(hd0)   /dev/hdb
(hd1)   /dev/sda
heinzbitte@ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1747    14032746   83  Linux
/dev/hdb2            1748        1826      634567+   5  Extended
/dev/hdb5            1748        1826      634536   82  Linux swap / Solaris

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        2167    17398395    f  W95 Ext'd (LBA)
/dev/sda2            2168       14851   101884230    b  W95 FAT32
/dev/sda5               2        2167    17398363+   7  HPFS/NTFS

```
I don't know if this helps or not.

---

### Post by Herman on 2006-04-08
Sure you can just add it right to /boot/grub/menu.lst if you want, it will be a little bit slower if it doesn't work and you have to try again, that's all. I looked at that info you provided and came up with the following, but it's pretty early in the morning for me, so I hope it's right:
```
title                      Windows XP
root                     (hd1,4)
map                     (hd0) (hd1)
map                     (hd1) (hd0)
savedefault    
makeactive
chainloader +1      
``` Good luck with it, I'm going back to sleep until the rooster crows, bye for now,  from Herman

---

### Post by Herman on 2006-04-08
Hello again, Heinzbitte, I was browsing around the forums here and found [this post]("http://www.ubuntuforums.org/showpost.php?p=903040&postcount=4") by sn123 about having the 'map' commands before the 'root' command.  The information by sn123 is probably right and mine is probably wrong, sorry for any inconvenience. Try:
```
title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,4)
savedefault
makeactive
chainloader +1
``` and see if that one works better. I don't have any computers here with more than one hard-drive each so I can't try these myself to prove whether they are right or not. Regards, (Herman).

---

