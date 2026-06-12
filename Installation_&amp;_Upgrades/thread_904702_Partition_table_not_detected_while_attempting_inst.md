---
title: "Partition table not detected while attempting installation"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by Steveire on 2008-08-29
Hi,

I currently use gutsy, and want to do a fresh hardy install.

I tried a hardy, gutsy, and an intrepid cd, but none of the installers detect my existing partition table.

[[IMG]http://img523.imageshack.us/img523/602/installpartitiontablemivu1.th.png[/IMG]](http://img523.imageshack.us/my.php?image=installpartitiontablemivu1.png)

Here's fdisk output

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       14267       14594     2620416    c  W95 FAT32 (LBA)
/dev/sda2              16        1321    10485760    7  HPFS/NTFS
/dev/sda3   *        1321        3752    19531250    7  HPFS/NTFS
/dev/sda4            3753       14594    87081357+   f  W95 Ext'd (LBA)
/dev/sda5           14267       14594     2620416   dd  Unknown
/dev/sda6            3753        4360     4883728+  83  Linux
/dev/sda7            4361       13901    76638051   83  Linux
/dev/sda8           13902       14266     2931831   82  Linux swap / Solaris

Partition table entries are not in disk order


```

sda6 is my gusty root partition
sda7 is my home partition
sda5 is a Dell MediaDirect thing.
sda1 seems to be the exact same thing.
sda3 seems to be windows vista
sda2 is a recovery partition
sda4: I have no idea what this is.

Here's a thread which seems to describe the same issue:

[http://ubuntuforums.org/showthread.php?t=780113](http://ubuntuforums.org/showthread.php?t=780113)

The answer given is 'use testdisk', but there is no instruction on what to do with it.

Here's what I tried:

```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


TestDisk is a data recovery designed to help recover lost partitions
and/or make non-booting disks bootable again when these symptoms
are caused by faulty software, certain types of viruses or human error.
It can also be used to repair some filesystem errors.

Information gathered during TestDisk use can be recorded for later
review. If you choose to create the text file, testdisk.log , it
will contain TestDisk options, technical information and various
outputs; including any folder/file names TestDisk was used to find and
list onscreen.

Use arrow keys to select, then press Enter key:
[ Create ]  Create a new log file
[ Append ]  Append information to log file
[ No Log ]  Don't record anything

```

**Click create**

```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

  TestDisk is free software, and
comes with ABSOLUTELY NO WARRANTY.

Select a media (use Arrow keys, then press Enter):
Disk /dev/sda - 120 GB / 111 GiB









[Proceed ]  [  Quit  ]

Note: Disk capacity must be correctly detected for a successful recovery.
If a disk listed above has incorrect size, check HD jumper settings, BIOS
detection, and install the latest OS patches and disk drivers.

```

**Click proceed**

...
Select intel (Don't know if that's right)
Select analyse

```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * FAT32 LBA            14266 230 45 14593  33 32    5240832 [MEDIADIRECT]
 2 P HPFS - NTFS             15  10 60  1320 117 13   20971520 [RECOVERY]
 3 * HPFS - NTFS           1320 117 14  3751 251 56   39062500 [OS]
 4 E extended LBA          3752   0 62 14593  33 32  174162715
Only one partition must be bootable
Space conflict between the following two partitions
 4 E extended LBA          3752   0 62 14593  33 32  174162715
 1 * FAT32 LBA            14266 230 45 14593  33 32    5240832 [MEDIADIRECT]
 5 L Sys=DD               14266 230 45 14593  33 32    5240832
   X extended              3752   0 63  4359 254 63    9767458
 6 L Linux                 3752   1  1  4359 254 63    9767457
   X extended              4360   0  1 13900 254 63  153276165
 7 L Linux                 4360   1  1 13900 254 63  153276102
   X extended             13901   0  1 14265 254 63    5863725
 8 L Linux Swap           13901   1  1 14265 254 63    5863662

*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition

```

Don't know what to do now. Is that message

> 
Only one partition must be bootable
Space conflict between the following two partitions


 important? I selected proceed, and got this:

```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    14 254 63     240912 [DellUtility]
P FAT32 LBA               15   0  1  4192 254 63   67119570 [NO NAME]
P Linux                 4360   1  1 13900 254 57  153276096
L Linux Swap           13901   1  1 14265 254 41    5863640
L FAT32 LBA            14266 230 45 14593  33 32    5240832 [MEDIADIRECT]








Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT16, 123 MB / 117 MiB


```

I press enter to continue.

```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63

     Partition                  Start        End    Size in sectors

 1 * FAT16 >32M               0   1  1    14 254 63     240912 [DellUtility]
 2 P FAT32 LBA               15   0  1  4192 254 63   67119570 [NO NAME]
 3 P Linux                 4360   1  1 13900 254 57  153276096
 4 E extended LBA         13901   0  1 14593 254 63   11133045
 5 L Linux Swap           13901   1  1 14265 254 41    5863640
 6 L FAT32 LBA            14266 230 45 14593  33 32    5240832 [MEDIADIRECT]









[  Quit  ]  [Search! ]  [ Write  ]

```

Then I click Quit. I seem to have come full circle.



Any advice?

---

### Post by Steveire on 2008-08-29
I'm guessing partitions 4 and 5 shouldn't be there at all.

Is that what testdisk is trying to tell me, and can testdisk fix it?

---

### Post by Steveire on 2008-08-29
I ran it again, and selected Search! to search deeper, and got this output:

```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    14 254 63     240912 [DellUtility]
D FAT32 LBA               15   0  1  4192 254 63   67119570 [NO NAME]
D HPFS - NTFS             15  10 60  1320 117 13   20971520 [RECOVERY]
D HPFS - NTFS           1320 117 14  3751 251 45   39062489 [OS]
D Linux                 3752   1  1  4359 254 62    9767456
D Linux                 3759   0  1  4366 253 62    9767456
D Linux                 4360   1  1 13900 254 57  153276096
P Linux Swap           13901   1  1 14265 254 41    5863640
P FAT32 LBA            14266 230 45 14593  33 32    5240832 [MEDIADIRECT]




Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT16, 123 MB / 117 MiB


```

It's quite different to the other output. Any ideas on what I need to do here?

---

### Post by Steveire on 2008-08-29
I found this thread:

[http://ubuntuforums.org/showthread.php?t=628229](http://ubuntuforums.org/showthread.php?t=628229)

It might be something to do with my issue.

---

### Post by Steveire on 2008-08-29
More interesting links:

[http://ubuntuforums.org/showthread.php?t=782810](http://ubuntuforums.org/showthread.php?t=782810)

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/953088.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/953088.html)

[http://www.dellideastorm.com/article/show/74178](http://www.dellideastorm.com/article/show/74178)

[http://ubuntuforums.org/showthread.php?t=606345](http://ubuntuforums.org/showthread.php?t=606345)

[http://newsgroups.derkeiler.com/Archive/Alt/alt.sys.pc-clone.dell/2008-05/msg01131.html](http://newsgroups.derkeiler.com/Archive/Alt/alt.sys.pc-clone.dell/2008-05/msg01131.html)

[http://www.linuxforums.org/forum/installation/83201-dell-mediadirect-messed-up-my-dual-boot-2.html](http://www.linuxforums.org/forum/installation/83201-dell-mediadirect-messed-up-my-dual-boot-2.html)

Next steps:

[LIST]
[*] Try the media direct button a few times, and see if things recover or break more
[*] Try the rmbr iso (found in the DellKit directory on the MediaDirect re-installation DVD apparently) and fixmbr/fixboot
[*] Reinstall grub and see if that works. [*] Try fixmbr
[*] Use testdisk, extended search, and remove the [NO NAME] and the middle linux partition.
[/LIST]

I'll try
```

rmbr 1 1

```
to make the mediadirect button function the same as the power on button.

I'll try to do this tomorrow with fresh eyes, but I'm still very confused, and hope someone else can shed some light on what's going on here and what I have to do.

Steve.

---

### Post by caljohnsmith on 2008-08-29
> **Steveire said:**
> ```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   [COLOR="Red"]*[/COLOR]       14267       14594     2620416    c  W95 FAT32 (LBA)
/dev/sda2              16        [COLOR="Red"]1321[/COLOR]    10485760    7  HPFS/NTFS
/dev/sda3   [COLOR="Red"]*[/COLOR]        [COLOR="Red"]1321[/COLOR]        3752    19531250    7  HPFS/NTFS
/dev/sda4            3753       14594    87081357+   f  W95 Ext'd (LBA)
/dev/sda5           14267       14594     2620416   dd  Unknown
/dev/sda6            3753        4360     4883728+  83  Linux
/dev/sda7            4361       13901    76638051   83  Linux
/dev/sda8           13902       14266     2931831   82  Linux swap / Solaris

Partition table entries are not in disk order

```
First problem I see is that in your fdisk output in your original post, it shows two partitions as being bootable; only one partition on a HDD should be marked as bootable or "active". Also, partition sda3 starts on the same cylinder as the end of sda2, not on the next one. And sda5 and sda4 are on top of each other. And... well the list goes on.

So bottom line is your partition table is quite messed up unfortunately.


> **Steveire said:**
> 
Next steps:

[LIST]
[*] Try the media direct button a few times, and see if things recover or break more
[*] Try the rmbr iso (found in the DellKit directory on the MediaDirect re-installation DVD apparently) and fixmbr/fixboot
[*] Reinstall grub and see if that works. [*] Try fixmbr
[*] Use testdisk, extended search, and remove the [NO NAME] and the middle linux partition.
[/LIST]

Reinstalling Grub or using "fixmbr" will unfortunately do nothing to fix your partition table. Can you mount any of those partitions, or even still boot into any of them? If you can, I would recommend saving important data right away. And you probably could use testdisk to somehow untangle the whole mess, but if it is at all a possibility, I would simply wipe the HDD clean and start over.

---

### Post by Steveire on 2008-08-30
> 
Reinstalling Grub or using "fixmbr" will unfortunately do nothing to fix your partition table. Can you mount any of those partitions, or even still boot into any of them? If you can, I would recommend saving important data right away. And you probably could use testdisk to somehow untangle the whole mess, but if it is at all a possibility, I would simply wipe the HDD clean and start over.

Hi,

Yes, I can use the vista and gutsy installations fine and I have backed up my data.

I want to try testdisk to fix it, but I can't find anyone who has actually used it to advise me on what to do in this case.

As far as I understand, I must have pressed the media direct button at some stage after installing gutsy. When it loads, mediadirect does 'ignorant writing' to the partition table - ignoring everything that's already there. 

It writes part of the partition table as it was in factory settings. It wrote sda4 (vista) covering cylinders 3753 to 14594, and sda5 (mediadirect) covering cylinders 14267 to 14594, and set it's label to unknown to hide it from vista. That's despite the fact that the partition is already there (sda1), albeit with a different label (maybe set by parted or grub when I installed gutsy). That is a strange overlap though. It also wrote a second bootable flag.

In any case, I'm going to try to run testdisk this morning with fresh eyes, remove the [NO NAME] and middle linux partitions, and set some logical and primary flags.


Thanks for the reply caljohnsmith.

---

### Post by Steveire on 2008-08-30
OK, I went for it and here's what happened

```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    14 254 63     240912 [DellUtility]
D FAT32 LBA               15   0  1  4192 254 63   67119570 [NO NAME]
P HPFS - NTFS             15  10 60  1320 117 13   20971520 [RECOVERY]
P HPFS - NTFS           1320 117 14  3751 251 45   39062489 [OS]
L Linux                 3752   1  1  4359 254 62    9767456
D Linux                 3759   0  1  4366 253 62    9767456
L Linux                 4360   1  1 13900 254 57  153276096
L Linux Swap           13901   1  1 14265 254 41    5863640
L FAT32 LBA            14266 230 45 14593  33 32    5240832 [MEDIADIRECT]




Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 10 GB / 10 GiB

```

```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63

     Partition                  Start        End    Size in sectors

 1 * FAT16 >32M               0   1  1    14 254 63     240912 [DellUtility]
 2 P HPFS - NTFS             15  10 60  1320 117 13   20971520 [RECOVERY]
 3 P HPFS - NTFS           1320 117 14  3751 251 45   39062489 [OS]
 4 E extended LBA          3752   0  1 14593 254 63  174176730
 5 L Linux                 3752   1  1  4359 254 62    9767456
 6 L Linux                 4360   1  1 13900 254 57  153276096
 7 L Linux Swap           13901   1  1 14265 254 41    5863640
 8 L FAT32 LBA            14266 230 45 14593  33 32    5240832 [MEDIADIRECT]







[  Quit  ]  [ Write  ]
                              Return to main menu

```

The recovery and OS partitions are too close for comfort really, meeting on the same cylinder, and what looks like consecutive blocks. I'm not sure exactly how to read those start/end columns.

I confirmed and saw this almost immediately:

```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


You will have to reboot for the change to take effect.



```

So, now I reboot

---

### Post by Steveire on 2008-08-30
Well, after rebooting I get a grub error 15, so back into a livecd for me. My fdisk -l looks like this:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          15      120456    6  FAT16
/dev/sda2              16        1321    10485760    7  HPFS/NTFS
/dev/sda3            1321        3752    19531244+   7  HPFS/NTFS
/dev/sda4            3753       14594    87088365    f  W95 Ext'd (LBA)
/dev/sda5            3753        4360     4883728   83  Linux
/dev/sda6            4361       13901    76638048   83  Linux
/dev/sda7           13902       14266     2931820   82  Linux swap / Solaris
/dev/sda8           14267       14594     2620416    c  W95 FAT32 (LBA)

```

And testdisk analyse reports this:
```

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 120 GB / 111 GiB - CHS 14593 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * FAT16 >32M               0   1  1    14 254 63     240912 [DellUtility]
 2 P HPFS - NTFS             15  10 60  1320 117 13   20971520 [RECOVERY]
 3 P HPFS - NTFS           1320 117 14  3751 251 45   39062489 [OS]
 4 E extended LBA          3752   0  1 14593 254 63  174176730
 5 L Linux                 3752   1  1  4359 254 62    9767456
   X extended              4360   0  1 13900 254 57  153276159
 6 L Linux                 4360   1  1 13900 254 57  153276096
   X extended             13901   0  1 14265 254 41    5863703
 7 L Linux Swap           13901   1  1 14265 254 41    5863640
   X extended             14266 229  1 14593  33 32    5240939
 8 L FAT32 LBA            14266 230 45 14593  33 32    5240832 [MEDIADIRECT]



*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition

```

Hopefully a grub install will give me a working installation again, and hopefully I can find some way of repartitioning correctly. I'm starting to think that the problem now is that OS and RECOVERY end and begin on the same cylinder. I'm not sure if that can be fixed if no partitioning tool is able to use the drive...

---

### Post by caljohnsmith on 2008-08-30
Your partition table looks great now except that as you pointed out, sda3 starts on the same cylinder as sda2 ends.

If you want to get Grub working again, I bet all you need to do is the following from the Live CD:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```

---

### Post by Steveire on 2008-08-30
I ran grub, but 
```

find /boot/grub/stage1

```

gave me a grub error 15 (file not found), so I followed instuction here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

```

ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/root /dev/sda5
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/root/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/root/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/root/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
ubuntu@ubuntu:~$ cat /mnt/root/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         1

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=575a68fe-7c6c-4aac-9589-372dbc3f5736 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=575a68fe-7c6c-4aac-9589-372dbc3f5736 ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=575a68fe-7c6c-4aac-9589-372dbc3f5736 ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=575a68fe-7c6c-4aac-9589-372dbc3f5736 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=575a68fe-7c6c-4aac-9589-372dbc3f5736 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Windows Vista/Longhorn (loader)
root            (hd0,2)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title           Microsoft Windows XP Embedded
root            (hd0,4)
savedefault
makeactive
chainloader     +1

ubuntu@ubuntu:~$  

```

---

### Post by caljohnsmith on 2008-08-30
It looks like you may have a dedicated Grub partition on sda5 (hd0,4). Try the following:
```
sudo grub
grub> find /grub/stage1
```
If that returns with (hd0,4), proceed with:
```
grub> root (hd0,4)
grub> setup (hd0)
```

---

### Post by Steveire on 2009-01-05
I'm really glad I put all the details into this post. A couple of days ago I had to use testdisk again to do the same fix.

By the way I fixed the partition issue at the time by using Acronis no Hirens Boot CD. It able to handle the partition boundaries being very close together, so I put some space between them and was able to install over my existing '/' partition.

Cheers,

Steve

---

### Post by DrGNU on 2009-05-13
> **Steveire said:**
> 
Any advice?

I am wondering what the conclusion to this was?
Were you able to repair your partitions?

I have a problem but only see ONE boot partition and need it to be a different partition.  I'm not able to mount the partition that I need (to back-up files in Vista).

To see what I am experiencing view this thread:
[http://ubuntuforums.org/showthread.php?p=7252450](http://ubuntuforums.org/showthread.php?p=7252450)

Thank you,

DrGNU (Steve)

---

