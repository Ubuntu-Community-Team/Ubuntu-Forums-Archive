---
title: "Dual-boot install, keeping original MBR w/ Grub on secondary partition..."
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by ThePenguinKnight on 2008-05-20
Howdy fellas (and gals). If a mod determines this thread be more appropriate in the Newbies or Laptop forums, feel free to move it, just please email me about it if you do.

I've got a Dell Inspiron 1520 laptop, been playing around with Linux (Ubuntu 8.04 and Mepis 7.0) the last few weeks, and I've been bitten by the bug. Dell's MediaDirect utility screwed over my last hard-drive, so I'm starting on a new factory-imaged drive. I still need my Windows XP for a few things, so I figgur I'll dual-boot and wipe the MediaDirect partition while I'm at it.

See [link.]("http://www.uluga.ubuntuforums.org/showthread.php?t=641609") 

This guy has done basically exactly what I want to do, but I'm getting a little confused when he says he installed GRUB to the boot sector of his extended partition. Still new enough that this one's tripping me up. 

(edit: My HDD is partitioned almost identically to the one listed in the first post of the linked thread. The only difference is that mine is slightly larger, 160Gb overall.)

I would like to have the primary power button boot the standard Windows MBR (meaning a straight boot into Windows), with the MD button (alternate power button) booting into Grub on my Linux partition. I understand and have successfully done the partitioning before, so I'm not worried about that; nor am I worried about assigning the spare button to access Linux, as this is a straightforward procedure as well (the two buttons can apparently call on different partitions to boot from).

What I need to know is how precisely to get Grub to install onto the Linux partition only, without wiping the default MBR. If I can get that to happen, I believe I can assign the MD button to boot Grub pretty easily. I figure it's probably a simple matter, but I'm still new to Linux and thought I'd try to run this past some gurus before I royally screw myself over again lol.

If you happen to know off-hand, I'd very much appreciate an explanation of the whys if you've got time, as well as the hows.

Any help is appreciated. Thanks in advance :)

---

### Post by meierfra. on 2008-05-20
If you post the output of

```
sudo fdisk -l
```
(l is a lowercase L)

I can give you detailed instruction.

---

### Post by ThePenguinKnight on 2008-05-21
I'm sorry, should've posted this to begin with:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       18620   149516955    7  HPFS/NTFS
/dev/sda3           18622       18947     2618595    f  W95 Ext'd (LBA)
/dev/sda4           18948       19457     4096575   db  CP/M / CTOS / ...
/dev/sda5           18622       18947     2618563+  dd  Unknown

```

-sda1 is some kind of Dell thing, probably the diagnostics utilities that their tech support guys are so fond of making their callers run.
-sda2 is Windows XP, with the MBR I'd like to keep intact.
-sda3 is a FAT32 "extended" partition. It appears to contain only sda5, which is Media Direct.
-sda4 is a Dell restore utility. Though it's kinda a dumb place to put it (I may later see if I can ghost that partition to my external hard-drive), I've used it once before and it does have some minor usefulness, so I don't mind hanging on to that one.
-sda5 is the MediaDirect 3.5 partition, the sleeping killer. This one I'd like to destroy entirely. 

As sda5 is a logical partition of sda3, I imagine I can simply delete this whole partition, reformat and expand sda3, and install Ubuntu there. This is the partition at which I'd like to place GRUB, as well. Later on, when I hit the "rmbr.exe" command to remap power keys, I can assign the MD button to call up GRUB at sda3. Assuming I understand it like I think I do, that is lol.

Thank you in advance, meierfra, and anyone else who may contribute. :)

---

### Post by meierfra. on 2008-05-21
I suggest to deleted sda5 and sda3. Then shrink  sda2.   From the unallocated  space create an extended partition. Inside the extended partition  create   an ext3 partition for root (/) and a swap partition. If you want you can also create a second ext3 partition for /home. The root partition  should be about 10GB, swap  twice your ram, but not more than 2GB (but if you use hibernation swap needs to be at least the ram) The rest for home.

During installation choose manual.

To install Grub to the extended partition, click on the advanced button in step 7 of the installation. Choose /dev/sda3 for the grub location.

(But double check that the extended partition still is /dev/sda3 after you did the partitioning. It might change to /dev/sda4)


Let me know if you need more details than this rough sketch.

---

### Post by ThePenguinKnight on 2008-05-21
> **meierfra. said:**
> I suggest to deleted sda5 and sda3. Then shrink  sda2.   From the unallocated  space create an extended partition. Inside the extended partition  create   an ext3 partition for root (/) and a swap partition. If you want you can also create a second ext3 partition for /home. The root partition  should be about 10GB, swap  twice your ram, but not more than 2GB (but if you use hibernation swap needs to be at least the ram) The rest for home.

During installation choose manual.

To install Grub to the extended partition, click on the advanced button in step 7 of the installation. Choose /dev/sda3 for the grub location.

(But double check that the extended partition still is /dev/sda3 after you did the partitioning. It might change to /dev/sda4)


Let me know if you need more details than this rough sketch.

Ok, I think I get it, but let me run through it once more so I'm clear before I do anything:

-Delete sda3&sda5 entirely.
-Shrink sda2 down to a good size (80-100Gb)
-From the resulting empty space, create a new sda3 extended partition, using ext3 formatting
-Inside sda3, make a 2Gb swap partition (sda 5) (I've got 2Gb of RAM, is the 2Gb swap big enough?)
-Make a partition for /home (sda6). I like the idea behind this one, but not sure on the implementation. Mainly I need to know if this one will be its own full partition or if I should make it inside sda3. I'll read up on it, but if you want to fill me in on the how-to I wouldn't mind. I imagine it should be a completely separate partition, but I'm still pretty new at this.
-Install Ubuntu at sda3 root and do something to get it to use sda6 as /home. No clue on getting /home to work, but I'll read up on it.
-And finally, use the Advanced tab on Grub and tell it to install to sda3 (I knew it was something simple lol).

After that, I'll use "rmbr.exe' to map the power buttons.

Have I got it mostly right?

Hopefully the amount of detail in this thread will help if I ever have to come back to this issue someday, or maybe somebody else wanting to do something similar and being similarly unlearned. Thanks again :).

---

### Post by meierfra. on 2008-05-21
> Delete sda3&sda5 entirely.
-Shrink sda2 down to a good size (80-100Gb)

Good so far.

> From the resulting empty space, create a new sda3 extended partition, using ext3 formatting

An extended partition does not have any format. It is just a container for other partitions.

> Inside sda3, make a 2Gb swap partition (sda 5) (I've got 2Gb of RAM, is the 2Gb swap big enough?)
2GB is fine ( I also have 2GB Ram and 2GB Swap, and my swap never gets used. So 2GB is plenty)

> Make a partition for /home (sda6). Mainly I need to know if this one will be its own full partition or if I should make it inside sda3. 

It has to be inside the extended partition since you can only have four primary partition (but it really is a full blown partition, it will behave just like a primary partition)


You also will need to create  ext 3 partition   for root  (/dev/sda7) inside /dev/sda3.


>  I like the idea behind this one, but not sure on the implementation. 
If you choose manual, you will be able to  assign mount points to your different partitions.   You need to assign "swap" to /dev/sda5", "/home" to /dev/sda6 and "/" to /dev/sda7. 

> 
Have I got it mostly right?

Yup, except  (as I already said) that you cannot use the extended partition for root, but need to create  one more partition.

---

### Post by ThePenguinKnight on 2008-05-21
Many thanks for clarifying. After shrinking sda2:

-Create the extended partition at sda3.
-Create 3 partitions inside sda3, one for swap (sda5- 2Gb), one for /home (sda6- some decent size, say 15Gb or so), and one for /root (sda7- the remainder).
-Install Grub to sda3.

It's a bit late, so I'll set to it in the morning. Thanks for the help, meierfra. :D

---

### Post by meierfra. on 2008-05-21
You got it. Just one thing: the mount point for your root partion is "/" and not "/root".
Also you might want to increase "/home". 20 GB should be more than plenty for "/"

I'm going to bed, too.

---

### Post by ThePenguinKnight on 2008-05-21
Ok, the partitioning, formatting, and install of Ubuntu 8.04 all went without a hitch. Problem: it didn't give me the options for GRUB when installing. GRUB over-wrote my MBR, which was pretty much the thing I was trying to avoid. >.>

Here's my drive now:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       11755    94373842+   7  HPFS/NTFS
/dev/sda3           11756       18947    57769740    5  Extended
/dev/sda4           18948       19457     4096575   db  CP/M / CTOS / ...
/dev/sda5           11756       12016     2096451   82  Linux swap / Solaris
/dev/sda6           12017       17238    41945683+  83  Linux
/dev/sda7           17239       18947    13727511   83  Linux

```

The system is functional, but it's not what I want it to be. I'm fairly certain the MediaDirect button is disabled now and can't hurt the computer (since it doesn't go anywhere), but I would like GRUB to be on sda3 and the original MBR on root. Frustrating...

I did have the foresight to backup the MBR before I started the process, so hopefully I can restore it and re-install grub to sda3. I'll have to look up how precisely to do that. If somebody's got a link or knows offhand the process, it'd probably speed things along. Thanks.

---

### Post by meierfra. on 2008-05-21
Installing grub to sda3 is easy:

Open a terminal in ubuntu (Applications->Accessories->Terminal)

Type

```
sudo grub 
```

and at the "grub>" Prompt:

```
root (hd0,6)
setup (hd0,2)
quit
```

(I'm assuming here that /dev/sda7 is your root partition)

Using you backup MBR can be tricky. Did you back it up after you did the partitioning or before? Make sure that you don't overwrite  the new partition table with the old one. If you want help with that, let me know exactly how you backed up the MBR.

Click on FiXMBR in my signature for some other option to restore the MBR.(although I'm not sure that they work with your "media direct button")

---

### Post by ThePenguinKnight on 2008-05-21
Ok, I installed GRUB to sda3 as you indicated. Easy enough...

The MBR backup was before the partitioning, while the drive looke like it did up in the first couple posts.

There's a chance, since the 'rmbr.exe' app installs the Dell MBR (the one I'm trying to keep), it might re-overwrite GRUB at sda, at which point I could have it chainload GRUB on sda3. Once again, more reading is required lol.

---

