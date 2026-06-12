---
title: "Trouble with GRUB loader on fresh server install"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by tsunamikitsune on 2010-09-25
I recently attempted to install Ubuntu Server 10.04, but ran into some problems during installation. An error telling me it wasn't able to install GRUB popped up and asked me if I wanted to continue, so I did, assuming I could figure it out later.

So, as far as I can tell, I have an Ubuntu install that I just can't get into.

I used a Live CD to try and install GRUB, but the best I've been able to manage is a GRUB prompt on boot and I have no idea how to make the Ubuntu happen. I'm not the smartest Linux guy, so the whole ordeal is getting me a little frustrated and I'm hoping someone can shine some light on the situation. Thanks in advance.

---

### Post by Rubi1200 on 2010-09-25
Use the LiveCD and post the results of the bootscript linked to at the bottom of my post please.

The results should show if there are problems and make offering solutions easier.

Thanks.

---

### Post by tsunamikitsune on 2010-09-25
Hope this helps. D:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       499,711       497,664  83 Linux
/dev/sda2             501,758   312,580,095   312,078,338   5 Extended
/dev/sda5             501,760   312,580,095   312,078,336  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        87b6626e-7d99-4e7d-af83-f6282526a792   ext2                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        VqPwGK-AxlT-Ku21-pZbq-BpYN-CTBZ-Fl09kJ LVM2_member                               
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/stage2
    .0GB: initrd.img-2.6.32-24-generic-pae
    .0GB: vmlinuz-2.6.32-24-generic-pae
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  64 ff ff ff 8d 86 d8 05  00 00 89 85 1c ff ff ff  |d...............|
00000010  8d 85 58 ff ff ff 89 44  24 08 8b 85 1c ff ff ff  |..X....D$.......|
00000020  c7 85 58 ff ff ff 00 00  00 00 c7 85 5c ff ff ff  |..X.........\...|
00000030  0d 00 00 00 c7 85 60 ff  ff ff 00 01 00 00 c7 85  |......`.........|
00000040  68 ff ff ff 00 01 00 00  c7 85 6c ff ff ff 00 00  |h.........l.....|
00000050  00 00 89 74 24 04 89 04  24 e8 1e 8d dc ff e8 bd  |...t$...$.......|
00000060  e8 dc ff 89 04 24 e8 e5  9e e0 ff 89 85 4c ff ff  |.....$.......L..|
00000070  ff 8d 86 0c 07 00 00 89  85 20 ff ff ff 8d 85 40  |......... .....@|
00000080  ff ff ff 89 44 24 08 8b  85 20 ff ff ff c7 85 40  |....D$... .....@|
00000090  ff ff ff 00 00 00 00 c7  85 44 ff ff ff 0e 00 00  |.........D......|
000000a0  00 c7 85 48 ff ff ff 00  01 00 00 c7 85 50 ff ff  |...H.........P..|
000000b0  ff 00 01 00 00 c7 85 54  ff ff ff 00 00 00 00 89  |.......T........|
000000c0  74 24 04 89 04 24 e8 11  75 dc ff e8 50 e8 dc ff  |t$...$..u...P...|
000000d0  89 04 24 e8 78 9e e0 ff  89 85 34 ff ff ff 8d 86  |..$.x.....4.....|
000000e0  40 08 00 00 89 85 24 ff  ff ff 8d 85 28 ff ff ff  |@.....$.....(...|
000000f0  89 44 24 08 8b 85 24 ff  ff ff c7 85 28 ff ff ff  |.D$...$.....(...|
00000100  00 00 00 00 c7 85 2c ff  ff ff 0f 00 00 00 c7 85  |......,.........|
00000110  30 ff ff ff 00 01 00 00  c7 85 38 ff ff ff 00 01  |0.........8.....|
00000120  00 00 c7 85 3c ff ff ff  00 00 00 00 89 74 24 04  |....<........t$.|
00000130  89 04 24 e8 94 aa dc ff  8d 46 04 c7 86 74 09 00  |..$......F...t..|
00000140  00 00 00 00 00 89 44 24  04 8b 46 04 89 04 24 e8  |......D$..F...$.|
00000150  48 8b dc ff 89 34 24 e8  34 ea ff ff c7 44 24 08  |H....4$.4....D$.|
00000160  00 00 00 00 c7 44 24 04  00 00 00 00 89 3c 24 e8  |.....D$......<$.|
00000170  78 6b dc ff 8b 86 74 09  00 00 c6 40 20 01 81 c4  |xk....t....@ ...|
00000180  fc 00 00 00 5b 5e 5f 5d  c3 89 85 0c ff ff ff 8d  |....[^_]........|
00000190  83 14 13 ff ff 89 06 89  34 24 e8 0d 6d dc ff 8b  |........4$..m...|
000001a0  85 0c ff ff ff 89 04 24  e8 cf a3 dc ff 89 85 0c  |.......$........|
000001b0  ff ff ff 8b 83 48 fa ff  ff 83 c0 08 89 86 00 3b  |.....H.........;|
000001c0  1d 1f 8e fe ff ff 02 00  00 00 00 f0 99 12 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Rubi1200 on 2010-09-25
Just to be clear, I have no experience with server installs.

However, I do see some problems here:

You say you tried to install 10.04 which uses GRUB2, but the results say that legacy-GRUB is installed 
> Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive      in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst. On the partition, I do not see the files nor an operating system.

Are you sure the install went through completely?

---

### Post by tsunamikitsune on 2010-09-25
I thought it did, but maybe I missed something somewhere.

The install went pretty normal until it tried to install GRUB, during which it failed. It asked if I wanted to continue (warning me I would not be able to boot into the OS without it). I did, assuming I couldn't really do much to fix it during the install and could deal with it afterwards.

So, to my knowledge, the OS should be on there, but without GRUB. Though my poor attempts to install it afterwards through online guides, most of which are probably based on Legacy GRUB and not GRUB2, gave it some semblance of an install, as I can get to a GRUB prompt after powering on the computer, but nothing else.

Should I try reinstalling the OS and see if the same thing happens?

---

### Post by Rubi1200 on 2010-09-25
Let's try first reinstalling GRUB2 since you used the 10.04 server edition:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

The first method is the easiest, but in your case if that does not work try Method 3: CHROOT.

Make sure you mount the right partition and install GRUB to the MBR of sda.

EDIT: I see you have LVM; did you follow the instructions in this guide (advanced installation)?
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

### Post by tsunamikitsune on 2010-09-25
Is LVM possibly the issue? I don't actually know what it does or why I would have installed it. After following your instructions to reinstall GRUB, I only get a slightly different GRUB prompt on boot.

---

### Post by Rubi1200 on 2010-09-25
> **tsunamikitsune said:**
> Is LVM possibly the issue? I don't actually know what it does or why I would have installed it. After following your instructions to reinstall GRUB, I only get a slightly different GRUB prompt on boot.
> Is LVM possibly the issue?Could well be.

Since you obviously have not made any major changes it might be best to simply reinstall from the beginning (though I would first wipe the drive clean to make sure nothing funny remains).

Read the guide I linked to previously and if you get stuck as before, stop and post here so someone can hopefully walk you through any problems. And check to make sure when you install that this LVM thing is not installed automatically.

By the way, do you have a RAID setup?

It might also be a good idea to ask any questions, especially related to this current problem we have been working on, in the Server Platforms sub-forum.

---

### Post by tsunamikitsune on 2010-09-25
Well, I'll try reinstalling then. I don't have time at the exact moment, but as soon as I do, I'll be sure to come back here with any problems.

I currently have one 160GB IDE hard drive in the computer for the OS, but I hope to later add two 1.5TB SATA drives in RAID for file storage. That's something that I currently have no idea how to set that up, so any advice on that is welcome as well. I'm hoping to mirror the two of them (RAID1, I think?) so if one dies, I can replace it and continue the RAID without losing any data (that is how it works, right?).

Anyway, thank you for all your help. I've been a pretty smart Windows user for much of my life (which isn't hard, I suppose), but whenever I come back to Linux, I find myself having to learn a lot of new stuff. Hopefully I learn more and find a way to handle it better in the future.

---

