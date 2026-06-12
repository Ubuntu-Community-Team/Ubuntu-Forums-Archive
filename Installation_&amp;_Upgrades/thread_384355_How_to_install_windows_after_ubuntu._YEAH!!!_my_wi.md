---
title: "How to install windows after ubuntu. YEAH!!! my windows install broke"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by tikal26 on 2007-03-14
Hello, I am looking for a way to install windows after ubuntu without messing with my Ubuntu. My XP installation broke and I have to reinstall ,but in al the articles Ire ad they alwaya say that I should install windows before Ubuntu.  Any help would be appreciated it

---

### Post by raul_ on 2007-03-14
There are a lot of threads about it in the forums. Anyway, the thing is that Windows installs MBR over Grub, so you'll have both OSs installed but you can't choose which one to boot. The trick is reinstalling Grub after you install windows. You have to use the Live CD and write some things in the command line...

Sorry but i don't remember what are the commands. Just search "Reinstall grub" in the forums or in google. Sorry but i don't have the time to search =\ it's just to give you the idea :)

---

### Post by Kateikyoushi on 2007-03-14
Not the end of the world, install windows as you would, but after that follow the instructions to reinstall grub. [LINK]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub")

---

### Post by tikal26 on 2007-03-14
Ok thanks that was not so hard

---

### Post by Schnare on 2007-11-15
I'm having a similar problem, except I can't load the XP setup 
it just won't run. any thoughts?

---

### Post by djbon2112 on 2007-12-19
> **Kateikyoushi said:**
> Not the end of the world, install windows as you would, but after that follow the instructions to reinstall grub. [LINK]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub")

I did this but the Windows install doesn't show up in the Grub loader. I tried adding it manually but I keep getting an "Invalid device requested" error.

Is there a way to manually add the Windows entry to Grub? I don't want to reinstall Ubuntu right now...

What I did (step by step):

1. Had Ubuntu Gutsy installed on my PC. Had modified the Grub menu.lst file myself to change the ordering and rename the stuff on the menu.
2. Created a new NTFS partition
3. Installed Windows XP Professional on that NTFS partition.
4. Booted off the liveCD and followed those steps to reinstall grub.
5. Rebooted, but the XP install wasn't listed in Grub.
6. Boot into Ubuntu, edit the menu.lst to add "Windows XP" and point it at the partition, still doesn't show up.

This is what I have under the menu.lst file, it's probably just broken, but if anyone can fix it, that would rock!:

```
[some stuff before]

title		Ubuntu "Gutsy Gibbon"
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=fd58961f-ecc5-4b47-af11-82682715eda3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Windows XP
root		(hd0,8)
makeactive
chainloader	+1

## title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
## root		(hd0,5)
## kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=fd58961f-ecc5-4b47-af11-82682715eda3 ro single
## initrd		/boot/initrd.img-2.6.22-14-rt

[some stuff after]
```

(hd0,5) is my Ubuntu partition, and (hd0,8 ) is my Windows partition. Under sudo fdisk -l they show up as /dev/sda5 and /dev/sda8 respectively. I tried changing the partition number of the XP one around (in case there's a mismatch somewhere) but I keep getting the error.

---

### Post by rsambuca on 2007-12-19
I don't think Windows will run from an logical partition.

---

### Post by djbon2112 on 2007-12-19
It's running from a logical partition inside an extended partition, but that doesn't matter, from my experience with Windows. It seems to be a problem with my Grub list but I don't know anything about it or how to configure it.

---

### Post by meierfra on 2007-12-19
djbon2112: How did you install Windows to the logical partition?  

as far as I know there are only two ways:

1)  You have (or used to have)  a second windows partition, which is a primary partition and contains the boot information.

2)  You installed windows on a primary partition and copied or moved the primary partition to a logical partition.


In case 1) you need to boot  through that primary partition (post the output of "sudo fdisk -l" for help). If you deleted that primary partition you will have to either reinstall Windows on a primary partition  or  move your logical partition to a primary partition.

In case 2) this should work:

title Windows XP
root (hd0,7)
chainloader +1

This assumes that windows is on sda8  (which is   (hd0,7) in grub notation)
Do not use "makeactive". "makeactive" does not work on logical partition.

---

### Post by djbon2112 on 2007-12-20
I created a second NTFS partition, and just ran the Windows XP installer, installing it to that device. The partition was primary when I did this, and it booted in the first time (before I repaired Grub).

As for sudo fdisk -l, 

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2   *          12        1317    10490445    7  HPFS/NTFS
/dev/sda3            1318       19458   145710221+   f  W95 Ext'd (LBA)
/dev/sda4           19131       19458     2620416   dd  Unknown
/dev/sda5   *        1318        6040    37937434+  83  Linux
/dev/sda6            6041        6562     4192933+  82  Linux swap / Solaris
/dev/sda7            6563       18482    95747368+   7  HPFS/NTFS
/dev/sda8           18483       19130     5205028+   7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x484ab4b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512    7  HPFS/NTFS

```

UPDATE: I tried your suggestion in #2, it didn't give me an error, but it just sat there flashing a cursor after "Starting up ...".

And, everything is on primary partitions (sda4-8 ), surrounded by an extended partition(sda3), with the other two being parts of Dell's recovery tools. I don't know why, but this is how Dell did it and to fix that I would have to format the entire hard drive which I don't want to do. SDB is my external HDD so that shouldn't matter.

---

### Post by rsambuca on 2007-12-20
> **djbon2112 said:**
> I created a second NTFS partition, and just ran the Windows XP installer, installing it to that device. The partition was primary when I did this, and it booted in the first time (before I repaired Grub).

As for sudo fdisk -l, 

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2   *          12        1317    10490445    7  HPFS/NTFS
/dev/sda3            1318       19458   145710221+   f  W95 Ext'd (LBA)
/dev/sda4           19131       19458     2620416   dd  Unknown
/dev/sda5   *        1318        6040    37937434+  83  Linux
/dev/sda6            6041        6562     4192933+  82  Linux swap / Solaris
/dev/sda7            6563       18482    95747368+   7  HPFS/NTFS
/dev/sda8           18483       19130     5205028+   7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x484ab4b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512    7  HPFS/NTFS

```

UPDATE: I tried your suggestion in #2, it didn't give me an error, but it just sat there flashing a cursor after "Starting up ...".

And, everything is on primary partitions (sda4-8 ), surrounded by an extended partition(sda3), with the other two being parts of Dell's recovery tools. I don't know why, but this is how Dell did it and to fix that I would have to format the entire hard drive which I don't want to do. SDB is my external HDD so that shouldn't matter.

I am afraid that your sda4 to sda8 are not primary partitions, they are logical partitions contained in the extended partition sda3.  It will be extremely difficult for you to get Windows to boot from within one of these logical partitions.

---

### Post by meierfra on 2007-12-20
Try 

title Windows XP
rootnoverify (hd0,1)
chainloader +1

If this does not work you might also try

title Windows XP
rootnoverify (hd0,6)
chainloader +1

andtitle Windows XP
rootnoverify (hd0,7)
chainloader +1


Are you able to boot into ubuntu?  menu.lst says "root (hd0,5)"  but according to fdisk ubuntu is on sda5, which is (hd0,4). Maybe you partition table is messed up.

Just for your information: sda5 -sda8 are logical partition (inside sda3). But sda4 is a primary partition.  Do you know what is on sda4?

---

### Post by meierfra on 2007-12-20
You partition table is definitely messed up. Any thing numbered sda1 to sda4 is  a primary partition.   But according to fdisk sda4 sits inside sda3, which makes it logical partition. So if none my suggestion from the previous post work, you should try to fix your partition table with testdisk (see my signature).

---

### Post by djbon2112 on 2007-12-20
Yea I agree it's quite messed up. I'd try fixing it too but Gparted just tells me my entire disk is free space... :(

I'm going to try those other options now, see if I can get it working. If not, I might have to wipe the entire disk.

Is there an easy way to back up my Ubuntu install? I've done quite a lot to configure and set it up, I really don't want to have to start from scratch :(

---

### Post by djbon2112 on 2007-12-20
Well, I tried your first suggestion, 

```
title Windows XP
rootnoverify (hd0,1)
chainloader +1
```

... and it worked! No idea why or how, but I'll take a hacked solution for now, until I have time to fix my partition table. Thanks!

---

### Post by meierfra on 2007-12-20
Actually this is not a hacked solution. If you install windows on a logical partition, windows  stores the boot information on the boot sector of a suitable primary partition. It  seems that /dev/sda2 was deemed suitable by Windows. As a result you can boot windows by chainloading /dev/sda2 (that is hd0,1). Chainloading (hd0,1) just  means that the boot sector of (hd0,1) is put in charge the booting process.


Your partition table is still messed up and you might run into problems next time you reinstall something  or repartition your hard drive. But as long as everything is working, I wouldn't worry about it now.

---

### Post by OldManRiver on 2007-12-20
Why not just install the XP under VM-Ware so it runs inside the Linux boot?

OMR

---

### Post by rsambuca on 2007-12-20
> **djbon2112 said:**
> Well, I tried your first suggestion, 

```
title Windows XP
rootnoverify (hd0,1)
chainloader +1
```

... and it worked! No idea why or how, but I'll take a hacked solution for now, until I have time to fix my partition table. Thanks!

Wow.  It is great you got it working, but to be frank, I really don't understand exactly how you did it, nor do I understand your partition table became so 'interesting'!

---

### Post by rsambuca on 2007-12-20
> **OldManRiver said:**
> Why not just install the XP under VM-Ware so it runs inside the Linux boot?

OMR

There are lots of instances where dual booting can be preferential to a virtual environment.  Performance is definitely a big one, especially if resources are light.  Some peripheral devices do not work properly inside of a virtual environment, and not all programs work perfectly inside of a virtual environment.

---

### Post by djbon2112 on 2007-12-20
> **rsambuca said:**
> There are lots of instances where dual booting can be preferential to a virtual environment.  Performance is definitely a big one, especially if resources are light.  Some peripheral devices do not work properly inside of a virtual environment, and not all programs work perfectly inside of a virtual environment.

Exactly. I'm going to be gaming with this install, so I want the best performance I can get. Gaming under VMWare is painful to watch >.<

---

