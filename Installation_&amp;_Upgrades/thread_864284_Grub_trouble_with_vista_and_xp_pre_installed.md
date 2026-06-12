---
title: "Grub trouble with vista and xp pre installed"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by clint1010 on 2008-07-19
OK, this is going to seem long winded but I'll try to explain what I have done.

Originally I had Ubuntu 7.04 installed on my machine, dual booting with XP happily for about 2 years off the same drive. I also have a second SATA drive for data storage (one 320Gb partition).

I my infinite wisdom I unplugged both SATA drives and plugged in a new 160Gb IDE drive to install a fresh copy of XP (original was corrupt) and a newly obtained copy of Vista. Installed XP first, no worries, then installed Vista, no worries. Vista installed a boot loader that let me select between the 2 and it all worked well. Once all that was OK, I then plugged back in my 2 SATA drives, then proceeded to install Ubuntu 8.04 on the original disk I had 7.04 on. I deleted all partitions off the disk (XP  and Ubuntu 7.04) and made 2 partitions, one EXT3 for / and the other a 4Gb swap. The install went well, Ubuntu runs as good as ever, but now on the Grub boot loader I have a list item for Vista/longhorn and when I select it I get an error 21 "disk doesn't exist" or similar.

I have tried a few things in the grub menu.lst file but with no luck, the file is now back in the original state.

here is the result of fdisk -l

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9726    78124063+  83  Linux
/dev/sda2            9727       10212     3903795   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007faa3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd76bd76

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sdc2            6375       19458   105089024    7  HPFS/NTFS

```

sda1 is Ubuntu 8.04 / (SATA)
sda2 is swap obviously (SATA)
sdb1 is the storage drive (SATA)
sdc1 is XP (IDE)
sdc2 is Vista (IDE)

Can anyone shed some light on what the problem might be before I blaze on  with mbr repair on the windows partitions please?

also, here is the vista entry in menu.lst:

```
title		Windows Vista/Longhorn (loader)
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

Any help would be much appreciated

---

### Post by clint1010 on 2008-07-19
Update:

If I set the first boot HDD in the BIOS to be sda, I get GRUB and can only boot Ubuntu, the windows entry fails with error 21.

If I set the first boot HDD in the BIOS to be sdc, I get the windows bootloader and can select to boot XP or Vista. Both windows systems have been proven to work OK

I have been changing the windows entry in menu.lst with suggestions I've found here on the forum with no luck.

The hunt continues ...

---

### Post by Pumalite on 2008-07-19
Change 'root' for Vista to (hd2,1)

---

### Post by clint1010 on 2008-07-20
thanks for the reply Pumalite. I just tried that change and still get an error 21 "selected disk does not exist".

This still has me baffled as when I change the BIOS HDD boot order between drives, all operating systems boot no problem, so there is nothing wrong with the MBR.

I think my mistake was to install both XP and Vista with the other drives removed.

Think I need to examine the grub manual.

Anyone else feel free to share your thoughts

---

### Post by Pumalite on 2008-07-20
ttp://users.bigpond.net.au/hermanzone/p15.htm

---

### Post by sandysandy on 2008-07-20
try updating GRUB. have a look here

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

regards

---

### Post by logos34 on 2008-07-20
> **clint1010 said:**
> I just tried that change and still get an error 21 "selected disk does not exist".
...

Anyone else feel free to share your thoughts

the windows boot files should be on sdc1 (you installled vista after xp, so it would have put them on the 'active' partition.

I think Grub just got the bios order of the disks wrong (common in mixed sata/ide systems)

Try:

>  title        Windows Vista/Longhorn (loader)
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by clint1010 on 2008-07-21
> **logos34 said:**
> title Windows Vista/Longhorn (loader)
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

No success with this edit, I also replaced hd1 with hd2 and no luck there either.

Might try setting up Grub again as SandySandy suggested

---

### Post by logos34 on 2008-07-21
> **clint1010 said:**
> No success with this edit, I also replaced hd1 with hd2 and no luck there either.

Might try setting up Grub again as SandySandy suggested

I doubt reinstalling grub to the mbr is going to help--grub stage1 is finding stage2 and menu.lst on the root partition fine...You can boot ubuntu.  The problem is specifically the windows entry.

We know for sure that grub is on the MBR of /dev/sda.  And you can boot XP and Vista directly without issue (via the vista boot manager).  But when sda is the boot drive, there can only be two possible Bios locations for the windows disk, /dev/sdc: (hd1) or (hd2).  And you need the mapping to perform a 'virtual swap' when chainloading windows on a second or third drive.  So either (hd1,0) or (hd2,0) + map lines should work.  When you install vista after XP, it takes over management of the boot process and locates the boot files on the prexisting active primary partition.  That's why in the fdisk output the XP and not Vista partition has the boot ('*') flag.  So I'm not sure why one of those entries doesn't work.  You could try changing the /boot/grub/device.map to correspond to the changes you make to windows root line in menu.lst, but that usually doesn't affect matters.  Or try 'rootnoverify' instead of just 'root'.

---

### Post by Pumalite on 2008-07-21
Did you disconnect the other drives when you installed?

---

### Post by clint1010 on 2008-07-22
> **logos34 said:**
> Or try 'rootnoverify' instead of just 'root'.

Thanks for the info Logos34, much appreciated. I have tried the following entries as you suggested:

```
title 		Windows Vista/Longhorn (loader)
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader +1
```

and

```
title 		Windows Vista/Longhorn (loader)
rootnoverify	(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader +1
```

and now I get an error "NTLDR is missing" not "selected disk does not exist". I assume that is due to the "rootnoverify" command.

I have been reading about the hide and unhide command for use in menu.lst was wondering if I could hide hd0 and hd1 if booting hd2? and will I still need to map hd2 to hd0?

@Pumalite
Yes, both SATA drives were disconnected when I installed XP and Vista on the IDE drive.

Thankyou both for trying to help me out.

---

### Post by logos34 on 2008-07-22
> **clint1010 said:**
> 
I have been reading about the hide and unhide command for use in menu.lst was wondering if I could hide hd0 and hd1 if booting hd2? and will I still need to map hd2 to hd0?

No, that doesn't apply to you because you did the default installation of windows, which relocates/consoldates the boot files on the older partition (with Vista bootloader in charge).  To use it you would have had to 'hide' the older partition (XP) before Vista installation so that the boot files for each OS remained on their own partition.  

One of those variations on the mapping should have worked.

You know, Grub doesn't always work with Vista, which is why some people end up dual booting using Vista bootloader -- get [EasyBCD.]("http://neosmart.net/wiki/display/EBCD/Linux")

Either that or continue to toggle the boot drive in the Bios to get into either OS.

---

### Post by Pumalite on 2008-07-22
I might have missed it, but could you post:
sudo fdik -lu

---

### Post by clint1010 on 2008-07-23
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9726    78124063+  83  Linux
/dev/sda2            9727       10212     3903795   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007faa3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd76bd76

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sdc2            6375       19458   105089024    7  HPFS/NTFS
```

No matter what commands I set in Grubs menu.lst I can't seem to get the machine to boot from hd2,0 (sdc1).

It might be the way my BIOS identifies the IDE HDD sdc? I don't really know

I'm going to try out EasyBCD as logos34 has suggested. Will post the results

[This link]("http://community.zdnet.co.uk/blog/0,1000000567,10008452o-2000498448b,00.htm") has also provided me some insight

Thanks for your input

---

### Post by Pumalite on 2008-07-23
Take a look at this bug report:
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497)

---

### Post by clint1010 on 2008-07-27
I have installed EasyBCD for Vista, which is s GUI to modify Vistas bootloader and if I boot from the windows IDE HDD to get the Vista bootlaoder, I can boot any OS from there. If I select Ubuntu from the vista bootloader, it directs to my linux HDD and I get the Grub bootloader, then I can get Ubuntu. Thanks for the suggestion with EasyBCD.

However, almost every time I boot into Ubuntu, the HDD labels change. Its like the HDDs are being presented to the OS in a diferent order. Eg. If sda is the Linux disk, sdb is the windows disk and sdc is the storage disk. Almost every time I boot these sd labels change. Eg. sda will be windows disk, sdb will be storage disk and sdc will be Linux. There is no pattern as to how the labels change. The order does not change for vista or XP, only Linux. And I've checked the BIOS and the order is not being changed there either. I have never come accross this before and its quite anoying as I have made an entry in fstab for my storage drive sdc to auto mount, but it mounts the wrong drive when the order changes.

weird ??



> Did you disconnect the other drives when you installed?
Yes, when I installed XP and Vista both SATA drives were disconnected.

All drives were connected when I installed Ubuntu, and Grub found the Vista Longhorn bootloader and made an entry for it.

---

