---
title: "grub. how fix it?"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by jeditalian on 2009-11-20
how do you tell grub what folder in hd0,1 to look for a particular operating system, if you have 2 or 3 operating systems on hd0,1? 
for example: ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Professional x64 Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 5e202dfc202ddc31
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
that one works, but theres another windows that is 32 bit so i can use my samsung pc studio, and its also at hd0,1 but the windowsfolder is the windows.0 folder. 
i installed it after ubuntu and got the ubuntu grub back instead of the original boot loader that it reverted to after installing windos. (which didnt even take 15 minutes since i didnt have to format the partition first.)
 so theres my problem. i am guessing that the location is there where it says set 5e09re09re90gtu349i 
ok i just hit abunch of keys but you see the menuentry above.
and the default bootloader consists of: [B][boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0="Microsoft Windows XP Professional" /fastdetect /noexecute=optin 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect 
i could have added ubuntu into that one, couldnt i? but grub has all that extra goodstuff like press e or c to do stuff.
[/B]

---

### Post by oldfred on 2009-11-20
If you have multiple windows installs they combine their boots into one partition. Grub can only chainload to that partition and from there you choose which windows to boot.

Windows copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

---

### Post by jeditalian on 2009-11-20
i dont really understand what you saying. initially, i installed xp64, downloaded ubuntu, burned the dvd, and installed them side by side. later, i got rid of everything, made a bunch of 50 G partitions , installed Ubuntu as the only operating system, needed some things that ubuntu cant offer, installed Xp64, got puppy linux later, it killed everything but xp64 including itself, so i deleted every partition except xp64 partition and my 700 somthing Gb backup partition.  installed puppy linux maybe to HD but at least to flash drive, but am not trying to make it dual boot with ubuntu. then i installed ubuntu. it has xp64 in the boot menu. then i needed something neither xp64 nor ubuntu has to offer, as far as i know. (to successfully connect my SGH-A877 to computer. ) so i installed windows xp pro ghetto edition. sure, i could install it to another partition and have it show up in grub, but i've never had any problems with dual booting two diff. os from the same partition before, and since grub is supposed to be superior, i figured it has its own way to do such a thing, but looking at grub.conf, it seems to me that either it only looks in one partition, or the path, which is easily distinguishable in the other file i showed you, is represented by some encrypted stuff or hex or something, whereas the one thats easily distinguishable knows the difference between the folders X and X.0

---

### Post by dddanmar on 2009-11-20
So you've got 

Harddrive

**Partition 1) **
C:\WINDOWS7
C:\WINDOWSXP
**Partition 2)**
UBUNTU
**Partition 3)**
LINUX SWAP

Grub will be available to give you the following options:

--
**Grub **
--
1) Windows Loader
2) Ubuntu

If you choose the Windows loader, grub will just boot to hd0,0 like you have already. 

What you will see then is

---
*Windows Loader*
--
1) Windows 7
2) Windows XP
--

What you need to look for is a boot manager for Windows that can handle different Windows installations on the same disk. 

I'm sure 7 or Vista or XP come with it but I've always installed my machines like:

**Partition 1) **
C:\WINDOWS7
**Partition 2)**
C:\WINDOWSXP
 **Partition 3)**
 UBUNTU
  **Partition 4)**
 LINUX SWAP

That way, you can have chainloader in your grub confid load each partition individually, also both partitions are visible to each other as they are both ntfs/fat32

---

### Post by oldfred on 2009-11-20
I did not know you could install 2 copies of windows to one folder. Grub just chainboots to the window boot loader in the partition boot record like the windows boot loader in the MBR does. Old grub cannot even read NTFS partitions, just jump there.

This is one way that just worked for another user. Install in two primary  partitions with the boot flag off to maintain the windows boot in the partition boot records.
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by jeditalian on 2009-11-20
ok yea i understand now. i went ahead and backed everything up to the big partition and deleted all the rest, reinstalled both windows then ubuntu and i see what you mean now. i  could have just added the windows loader into my grub. see, the grub entry was for xp64, not the loader. but a clean install never hurt anyone. plus, i made them all individual partitions again. and i am having so much less trouble with ubuntu, like the first time i installed it. there were some remnants of the first ubuntu install somewhere on one of those partitions the whole time giving me trouble. [SOLVED]
@oldfred: not the same folder, but the same partition. if i choose to setup a second copy of windows on the same partition, the first windows will have the C:/ windows folder, and the second will be a C:/WINDOWS.0 folder. 
i am going to change my boot graphics to WINBLOWS is BLOWING instead of loading, but it was so much easier to do that stuff with win95 and 98. now changing those graphics is really complicated
i would like to modify a windows installatino CD and replace all the graphics with something really F'd up too lol. oooooh or a rickrolling windows installation disc :) i would hate me so much if i gave that to me.

---

### Post by dddanmar on 2009-11-24
> oooooh or a rickrolling windows installation disc

You've been youtubing haven't you ;) Though...great idea! A bit of n/v-lite to change everything default to Rick. I love it.

[http://www.youtube.com/watch?v=5XOb1knVTZQ](http://www.youtube.com/watch?v=5XOb1knVTZQ)

---

