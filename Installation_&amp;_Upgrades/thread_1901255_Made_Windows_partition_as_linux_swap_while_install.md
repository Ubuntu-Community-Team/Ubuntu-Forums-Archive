---
title: "Made Windows partition as linux swap while installing Ubuntu. Now neither loads."
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by MajinSaha on 2011-12-28
Hello!
The subject describes most of my problem.
I had Win XP on part of my hard disk installed, it was NTFS. I tried to install Ubuntu 11.10 from a bootable USB and selected another partition for it. It asked me whether I wanted to specify partition for swap ( to make installation faster and blah-blah). I chose my Win XP partition for that ( there was no other choice ). Honestly, I thought there's no problem with that. Installation went smoothly after, as I thought.
When I tried to load... "Error loading operating system" on the top of the black screen... That's all. We didn't even get to the OS choice list. Just that line. WTF???
Ok, I loaded Ubuntu live and tried to get in contact with my hard drive through disk manager. It doesn't let me mount my Windows partition. Says it's a swap partition. I hope I didn't lose my information and it's still there but somehow I cannot get a hold of it. I hope I'm right...
Please let me know how I can recover my info. That's all I need. I don't need to install Ubuntu anymore. I've had enough with it...
I really appreciate your help!

---

### Post by 2F4U on 2011-12-28
Since you choose the Windows partition as swap, Ubuntu has formated it and thats why you can't access it any more. At least some part of the partition will be lost, but others may be recoverable. I would suggest that you look for professional help to recover your data.

---

### Post by darkod on 2011-12-28
"You've had enough with it???"

Just because you told it to use your windows partition as swap you are mad with ubuntu now??? So what if there were only two partitions, you can create a third one you know.

Anyway, you should be able to restore the partition with Testdisk. The manual is here: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You might want to ask a friend to help you. Otherwise we might see a post here that you've had it with testdisk too. But you will have to use it from ubuntu live mode since you have no other OS to boot. You can install it in live mode with:
sudo apt-get install testdisk

And run it with:
sudo testdisk

---

### Post by MajinSaha on 2011-12-28
Thanks. I will try to run testdisk and will tell you how it's going.
I've had enough with Ubuntu not because of what happened specifically. It was the last hit to my patience. Constant learning for several years didn't get me close to a feeling that I'm comfortable with Ubuntu. Some other problem pops up every time. Just saying.

---

### Post by fantab on 2011-12-28
> **MajinSaha said:**
> 
Please let me know how I can recover my info. That's all I need. I don't need to install Ubuntu anymore. I've had enough with it...


First of all CALM DOWN, RELAX. 
Yes, you've made a mistake when you created SWAP space by removing NTFS. Learning from mistakes is an excellent way to gain experience. From Now on ALWAYS BACK UP YOUR DATA before you try any partitioning. 

Now you have to regain your lost Data that was on the NTFS Partition. [COLOR=DarkRed]**darkod**[/COLOR] has pointed you to Testdisk and its manual. Read it carefully and follow instructions. I am sure you will be able to recover most of the lost DATA. 

Use UBUNTU LiveCD to access the internet. (If you don't know how to use LiveCD, When the live CD boots choose TRY UBUNTU). 

After you have done that see this **[info on Dual-Boot]("http://members.iinet.net.au/%7Eherman546/p23.html")**. 
Remember you should install WINDOWS FIRST, and then Ubuntu.

---

### Post by Mark Phelps on 2011-12-28
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by MajinSaha on 2011-12-28
The good news is that I managed to see the contents of my NTFS partition. All the files are there. Although I couldn't get testdisk via 
```
sudo apt-get install testdisk
```
since the package with such name could not be found, I nevertheless downloaded one from the link you provided(binary files) and run it. Without much of a reading on what to do, I analyzed the disk and it returned me my old content.
The next question is how to save this all, but I guess I can handle this since there are some "save" options provided.
Maybe I am asking too much, but is there a way to play with these files so that I could make that WinXP partition the same bootable one as it was before? Are you familiar with this low-level stuff?

Thanks for your advice on testdisk! This forum works way better than Ubuntu itself! :)

---

### Post by darkod on 2011-12-28
I thought the package existed, maybe I'm wrong.

Being able to list the files is definitely a good sign. Yes, it can save a new partition table with all partitions there, that's the point.

The steps in general go like:
1. First you scan with the Quick Search. I guess you already did that and it can list your files. When it lists the partitions found, you need to use the up/down arrows and select the XP partition, and then use the left/right arrows to change the letter at the beginning of the line into *.
The * sign means Primary partition with the boot flag on, which XP needs to be. After you change it to * press Enter (see first image attached). That will bring you to a screen listing partitions.
2. If in this list all partitions exist, just select Write to write the partition table. IMPORTANT: ONLY DO THIS IF ALL PARTITIONS ARE CORRECTLY LISTED!!! See second image attached.

After selecting write the new partition table is written and it contains the partitions that were listed by testdisk, that's why it's important the list to be correct before you select Write.

That's it. If you want to read more details, the exact procedure is here: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Note that if the quick search locates all the partitions, no need to do deeper search. Only if the quick search can't locate all of them, you use deeper search.

---

### Post by MajinSaha on 2011-12-29
I indeed had to use deeper search. Qucik one wasn't enough. Ok, before I press write, I will try to describe what I get in more detail, just to be sure.
And thanks for your help. Including pictures is really awesome!

---

### Post by MajinSaha on 2011-12-29
The partitions I see after deeper search are (I omitted some number columns on the right):
```
D Linux swap   0 1 1
D HPFS - NTFS  0 1 1
L FAT16 LBA    8355 1 1
```
So I make the second one with * on the left and then press Write? Is it fine that the first one is marked for deletion even though it coincides with the second?

---

### Post by darkod on 2011-12-29
Yes, you want to bring back the NTFS partition and you need to mark that one with *. The swap partition remains D - deleted because you don't want it. This will probably show some ubuntu errors until you delete the swap from within the ubuntu system, but the main goal here is to get XP back and the data.
No problem if ubuntu gives errors about swap.

PS. The second group of 3 numbers are important too. It goes like CHS - Cylinder - not sure what the H is for, maybe Head - Sector.
0 1 1 means starting at cylinder 0, head 1, sector 1
it should end on a cylinder too usually, like XXX 255 63
And then the next partition should start at XXX+1 1 1

Important is not to have any partitions overlapping so take a look at the numbers before doing the write, there should not be any partitions overlapping.

---

### Post by MajinSaha on 2011-12-29
I did it, but unfortunately my XP won't load. There's no line anymore that says "Error loading OS", but there is just blinking cursor at the top of the screen that never vanishes.
So I guess I have to forget about XP and try to save my files somehow while it's not too late.

---

### Post by darkod on 2011-12-29
The blinking cursor might be grub2.

Lets try if we can make XP boot at least. In the worst case you should be able to open the partition and save you data now from live mode.

Now the XP has the boot flag, so it should boot directly if we put standard bootloader on the MBR. You can do it from ubuntu live mode with:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

There will be some warnings, ignore them, it's normal.

Reboot and see if XP loads directly. If it does, we will deal with ubuntu later.

---

### Post by MajinSaha on 2011-12-29
I did what you said (lilo run without any bad warnings), but it made no effect. Should I maybe configure lilo correctly or something? Because it was telling me that I have to do it before running lilo.
Also, is it strange that when I run testdisk and start analyzing again, it doesn't see my NTFS anymore without performing deeper search again? It kinda wastes a lot of time to skan disk over and over.

---

### Post by darkod on 2011-12-29
No need to configure lilo, the message about configuring it was the warning to ignore.

If the partitions still don't look as they should, maybe the partition table wasn't written.

Lets see them, from live mode post the result of:

sudo fdisk -l (small L)

---

### Post by MajinSaha on 2011-12-29
This is the output:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfad7fad7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   134223074    67111506    7  HPFS/NTFS/exFAT
/dev/sda2       134223075   312560639    89168782+   f  W95 Ext'd (LBA)
/dev/sda5       134223138   312560639    89168751    e  W95 FAT16 (LBA)

Disk /dev/sdb: 4025 MB, 4025810432 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7862911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x046a0469

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          38     7839719     3919841    b  W95 FAT32

```
Note that I am running Ubuntu live from USB, so my USB drive is made bootable by default now.
Also, I executed fdisk command without executing testdisk. Do I have to run testdisk before that on each Ubuntu reboot? 
It takes me about 40 minutes to process analyzer in testdisk.

---

### Post by darkod on 2011-12-29
No, you don't need to run testdisk. The partition table looks fine now, look at the start-end sectors, sda2 continues immediately after sda1.

But some of the XP boot files might have been corrupted or missing during the transformation into swap partition. This could be a reason it's not booting windows.

From live mode you can follow the link in my signature to run the boot info script and post the results. The instructions are in the link too. That will show more details, most importantly if the XP boot files are there and if it's recognized.

In worst case, you can copy the data from sda1 in live mode to an external disk, and reinstall XP. At least the partition is back, it looks like it.

---

### Post by MajinSaha on 2011-12-29
This is the output of your program:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 12058 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   134,223,074   134,223,012   7 NTFS / exFAT / HPFS
/dev/sda2         134,223,075   312,560,639   178,337,565   f W95 Extended (LBA)
/dev/sda5         134,223,138   312,560,639   178,337,502   e W95 FAT16 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4025 MB, 4025810432 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7862911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        600E-4318                              vfat       PENDRIVE
/dev/zram0       cf584f56-5a09-41c3-8eab-15f09cc5ab99   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by darkod on 2011-12-29
Even though in fdisk it looks fine, the message at the beginning of the script says "unknown filesystem".

You could also try scanning the partitions with fixparts: [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

It can detect errors and repair them.

---

### Post by MajinSaha on 2011-12-29
@darkod,
thank you very much for your help! You've been very helpful and I'd be glad to give you many +1, if there was such option on this forum. 
I backed up my data successfully and will try to run FixParts within next few days. I will post the outcome here.

---

