---
title: "Windows 7 retitled ubuntu 10.04 partition as &quot;unallocated&quot;"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by avatarmonkeykirby on 2011-01-17
Hello,
I have been duel booting windows 7 and ubuntu 10.04, and wanted to do a fresh install of both. I decided that the easiest thing to do would be to take care of the Windows install first because installing it after always causes problems. I copied all my personal/work/school files onto the Ubuntu partition then proceeded with the installation. Redoing the Windows partitions went as planned however, Windows decided to relabel my Ubuntu partition as "unallocated" instead of ext4. This is bad. I am sure that I did not delete the ubuntu partition, so I'm fairly certain all my files are intact, just not accessible due to the mislabeling. Is there a way to reinstate the partition to ext4 without reformatting it?

output of fdisk -l[INDENT]     Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
    255 heads, 63 sectors/track, 121601 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x9dd2cb09

       Device Boot      Start         End      Blocks   Id  System
    /dev/sda1   *           1          13      102400    7  HPFS/NTFS
    Partition 1 does not end on cylinder boundary.
    /dev/sda2              13       69306   556595200    7  HPFS/NTFS
    Partition 2 does not end on cylinder boundary.
    /dev/sda3           69306      121601   420059913    5  Extended
    Partition 3 does not end on cylinder boundary.
    /dev/sda5          120473      121601     9064408+  82  Linux swap / Solaris
[/INDENT]As you can see it appears fine, however gparted gives a different story.
[https://sites.google.com/site/paulbakerlesaltshaker/GpartedScreenshot.png](https://sites.google.com/site/paulbakerlesaltshaker/GpartedScreenshot.png)
(sorry it is so large, I cannot modify it at this time)

So long story short, I cannot mount my linux partitions and I can't reformat them without losing their content. How can I fix them?

---

### Post by avatarmonkeykirby on 2011-01-17
Additionally: I don't mind if the way to do it is really unconventional or ugly, but if there isn't a way to do it without losing my data then I would like to know that too.

---

### Post by Quackers on 2011-01-17
Just an idea. From the live cd/usb desktop open gparted. Right-click on the space that should be your partition and see if you can check the filesystem. I suspect not, but it's worth a try.

---

### Post by Bucky Ball on 2011-01-17
Windows doesn't recognise EXT partitions natively at all so it would label them as 'unallocated'. Doesn't know what they are. ;)

---

### Post by Quackers on 2011-01-17
According to the screenshot gparted doesn't think much of it either :-)

---

### Post by Bucky Ball on 2011-01-17
> **Quackers said:**
> According to the screenshot gparted doesn't think much of it either :-)

Gotcha. Looks like Ubuntu has been 'disappeared'.

---

### Post by avatarmonkeykirby on 2011-01-17
Yes, I'm doing all of this through the live disk. The partition is no longer recognized by Ubuntu. Is there a way of reclassifying or remarking it as EXT without reformatting the whole partition?

---

### Post by Quackers on 2011-01-17
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by avatarmonkeykirby on 2011-01-17
The results of the script are as follows:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,113,397,247 1,113,190,400   7 HPFS/NTFS
/dev/sda3       1,113,399,294 1,953,519,119   840,119,826   5 Extended
/dev/sda5       1,935,390,303 1,953,519,119    18,128,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        944CE0224CDFFCBC                       ntfs       System Reserved               
/dev/sda2        ACACE22CACE1F0AE                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        a00008af-de69-4254-9889-db194ad23445   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  1e 59 a4 94 02 79 8a 51  d0 ed f9 2b 54 22 cf aa  |.Y...y.Q...+T"..|
00000010  72 b5 a9 39 3b 17 4b ef  48 8f ed 12 87 9e cd c6  |r..9;.K.H.......|
00000020  92 36 3a 59 ac 73 c8 6e  75 8e 53 1e f8 30 cd fb  |.6:Y.s.nu.S..0..|
00000030  6d 44 52 57 aa 19 3a fe  76 f8 bf 8e a3 ff eb fb  |mDRW..:.v.......|
00000040  1c ca bc 9c 8a a0 0a 12  c3 07 2d 5a c1 e7 0c 50  |..........-Z...P|
00000050  85 28 75 e2 f2 bb da 79  01 66 89 42 90 38 b6 d6  |.(u....y.f.B.8..|
00000060  4b 91 df 04 a2 f2 2b 00  e6 7f 5d 84 9f 4c ec 2d  |K.....+...]..L.-|
00000070  ce 3e 3e d5 dd 19 51 c6  da da 5c f8 9d 7c 3a f2  |.>>...Q...\..|:.|
00000080  f5 80 bb 9d 6f 9f 30 ab  d5 2b 95 02 ed 0d c6 f9  |....o.0..+......|
00000090  92 7e 0f 70 b7 09 66 21  07 6a f8 8c 82 56 97 0d  |.~.p..f!.j...V..|
000000a0  34 34 c5 8b c6 e6 c9 12  a8 22 2d f8 6c b3 87 41  |44......."-.l..A|
000000b0  fd 5a c6 52 0d 04 01 af  8d 77 89 34 ee 8b 8c e7  |.Z.R.....w.4....|
000000c0  95 ba 67 56 7c 41 99 34  b3 74 fa 68 6a da 97 48  |..gV|A.4.t.hj..H|
000000d0  e8 5f 1b 34 f4 f5 e3 8d  b0 92 5a d6 b5 6c c2 b1  |._.4......Z..l..|
000000e0  cd bb 95 3f f4 16 d6 6a  0e b9 ec da a5 86 f8 02  |...?...j........|
000000f0  af 21 6a 76 72 c7 ef 1c  9b 91 21 5d 0f cc 4c 9d  |.!jvr.....!]..L.|
00000100  60 e1 8b 84 c8 e1 77 36  94 0c aa 84 de 40 66 2c  |`.....w6.....@f,|
00000110  9e 3a 03 36 a0 3f 72 99  3f 61 88 49 12 3a 04 51  |.:.6.?r.?a.I.:.Q|
00000120  9d 94 50 5f 99 88 56 56  4d a8 e0 54 6d ef 3c 85  |..P_..VVM..Tm.<.|
00000130  9d a9 33 f4 46 aa 31 c6  f3 0b fc a6 ee 7b f3 9c  |..3.F.1......{..|
00000140  41 a1 f3 b2 af 6a bd f4  bb 5a fc 24 4a 45 74 a1  |A....j...Z.$JEt.|
00000150  79 53 a6 9b 2d 73 95 ff  67 fc ac 80 78 dd 2b cf  |yS..-s..g...x.+.|
00000160  a6 b2 7a 02 ae ed c6 27  0a 1a 7c 60 98 fc 66 26  |..z....'..|`..f&|
00000170  9b 5d d0 3b 35 67 41 a0  d5 67 7a bc 0c d8 f2 77  |.].;5gA..gz....w|
00000180  44 99 dd 78 95 24 16 22  4e ce 0c 32 7f 7c ed 14  |D..x.$."N..2.|..|
00000190  38 8c ed a7 79 46 96 e7  e2 d5 d8 39 e4 1c d6 18  |8...yF.....9....|
000001a0  aa f0 68 c6 ce b3 31 cd  7a db 5d 37 fd 1f 28 0b  |..h...1.z.]7..(.|
000001b0  2e 1a f2 02 b7 4e ac 39  94 35 dd 3c 5b 39 00 ef  |.....N.9.5.<[9..|
000001c0  ff ff 82 ef ff ff 61 96  fe 30 b1 9f 14 01 00 00  |......a..0......|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Quackers on 2011-01-17
I really don't know what has happened. But one thing seems certain and that is that the ext4 partition is no longer there.
gparted doesn't report its presence, the boot script doesn't and fdisk -l doesn't. It seems to have disappeared I'm afraid.
You could try testdisk/PhotoRec and see if anything can be recovered.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by srs5694 on 2011-01-18
TestDisk is probably the best option for a speedy recovery; however, it sometimes creates extended partitions that are too large (they extend beyond the disk's capacity), which then causes GParted and related tools to report that the disk is empty. I have a [Web page that describes how to fix this problem,]("http://www.rodsbooks.com/missing-parts/index.html") should you encounter it.

Before Using TestDisk, you might try this:


[LIST=1]
[*]Type "sudo fdisk /dev/sda" to launch fdisk. *Do not* launch it with the -u or -c option, though.
[*]Type "n" to create a new partition. Tell fdisk you want to create a logical partition and accept the default values for the start and end points.
[*]Type "p" to check the partition table. It should show a new logical partition that's quite large -- just a bit smaller than the extended partition.
[*]Type "w" to save your changes.
[*]Reboot your emergency disc.
[*]See if you can mount the new partition. If so, you're golden.
[*]If you can't mount the new partition, type "sudo blkid /dev/sda6" (assuming that's its number). The blkid utility attempts to identify the filesystem on the specified device.
[*]If blkid identified the partition as holding an ext2/3/4 filesystem (or whatever filesystem you used), try using fsck on it and try mounting it again.
[*]If you're still having no luck, launch fdisk again and type "d" followed by the partition number to delete it. Type "p" to verify that you deleted the right partition (if you didn't, exit by typing "q"), followed by "w" to save your changes.
[/LIST]


With any luck, you'll be able to recover your partition in this way; however, this isn't guaranteed. It's entirely possible that Windows moved the start point of the extended partition, or it might not start where it most likely does, either of which would prevent this operation from succeeding. If you're careful not to do anything destructive to the partition you create using fdisk, the risk is low, and if it works, recovery will be easy, so it's worth a shot. Just be very careful; you don't want to write data to the new partition (by using fsck or any other tool that writes data) unless/until you know it's valid.

---

### Post by presence1960 on 2011-01-19
First I am sorry about your files, I feel your pain. For future reference it is recommended that you back up your files **_on a different media_** whenever performing partitioning or OS installations.

Don't boot to your hard disk. Stay with the Live CD, because if you want a chance of recovering your stuff you do not want to write to the area where those files are. I know it is "unallocated" but since this happened already why take another chance?

Testdisk may be able to recover the lost partition. See [here]("http://www.cgsecurity.org/wiki/Running_TestDisk")

You can install it to the Live CD session by opening a terminal and running ```
sudo apt-get install testdisk
```

Once installed run in terminal ```
sudo testdisk
``` and follow the instructions from that link to recover the "lost" partition.

---

### Post by avatarmonkeykirby on 2011-01-19
Thanks for the replies everyone. Those last two where especially helpful, alas I actually fixed my issue with Quackers' suggestion.

My final resolution:
Using testdisk, I did a deep scan of my hard-drive. what it found was that Windows 7 had decided to write over a few cylinders onto the unbuntu partition. This was what made the ext4 partition unreadable, even via live-disk. So using testdisk I deleted the offending Windows Partition and restored the ext4 partition.
[The image below shows the overlap in partitions]
[IMG]http://sites.google.com/site/paulbakerlesaltshaker/testdisk.png[/IMG]

Ubuntu was not bootable because Grub2 had to be repaired. I followed the instructions to this guide: [http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7). Specifically the instructions for the live CD installation
```

sudo -i
mount /dev/sda3 /mnt grub-install --root-directory=/mnt/ /dev/sda
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys chroot /mnt
update-grub
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit

```
Grub2 was successfully restored, which allowed me to access my files which I've promptly dumped into my friend's external hard-drive.

I'm now going to wipe my drive and start completely fresh. I don't have a secondary drive of my own to permanently keep my files (like you suggested presence1960), so I'm going to have three partitions as my next configuration. 10 GB for Windows 7, 10 GB for Ubuntu 10.04, and the rest of the terrabyte will go to files that both systems can access.

Thanks for all your help again!:popcorn:

---

### Post by avatarmonkeykirby on 2011-01-19
Thanks for the replies everyone. Those last two where especially helpful, alas I actually fixed my issue with Quackers' suggestion.

My final resolution:
Using testdisk, I did a deep scan of my hard-drive. what it found was that Windows 7 had decided to write over a few cylinders onto the unbuntu partition. This was what made the ext4 partition unreadable, even via live-disk. So using testdisk I deleted the offending Windows Partition and restored the ext4 partition.
[The image below shows the overlap in partitions]
[IMG]http://sites.google.com/site/paulbakerlesaltshaker/testdisk.png[/IMG]

Ubuntu was not bootable because Grub2 had to be repaired. I followed the instructions to this guide: [http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7). Specifically the instructions for the live CD installation
```

sudo -i
mount /dev/sda3 /mnt grub-install --root-directory=/mnt/ /dev/sda
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys chroot /mnt
update-grub
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit

```Grub2 was successfully restored, which allowed me to access my files which I've promptly dumped into my friend's external hard-drive.

I'm now going to wipe my drive and start completely fresh. I don't have a secondary drive of my own to permanently keep my files (like you suggested presence1960), so I'm going to have three partitions as my next configuration. 10 GB for Windows 7, 10 GB for Ubuntu 10.04, and the rest of the terrabyte will go to files that both systems can access.

Thanks for all your help again!:popcorn:
__

---

### Post by avatarmonkeykirby on 2011-01-19
Thanks for the replies everyone. Those last two where especially helpful, alas I actually fixed my issue with Quackers' suggestion.

My final resolution:
Using testdisk, I did a deep scan of my hard-drive. what it found was that Windows 7 had decided to write over a few cylinders onto the unbuntu partition. This was what made the ext4 partition unreadable, even via live-disk. So using testdisk I deleted the offending Windows Partition and restored the ext4 partition.
[The image below shows the overlap in partitions]
[IMG]https://sites.google.com/site/paulbakerlesaltshaker/testdisk.png[/IMG]

Ubuntu was not bootable because Grub2 had to be repaired. I followed the instructions to this guide: [http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7). Specifically the instructions for the live CD installation
```

sudo -i
mount /dev/sda3 /mnt grub-install --root-directory=/mnt/ /dev/sda
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys chroot /mnt
update-grub
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit

```
Grub2 was successfully restored, which allowed me to access my files which I've promptly dumped into my friend's external hard-drive.

I'm now going to wipe my drive and start completely fresh. I don't have a secondary drive of my own to permanently keep my files (like you suggested presence1960), so I'm going to have three partitions as my next configuration. 10 GB for Windows 7, 10 GB for Ubuntu 10.04, and the rest of the terrabyte will go to files that both systems can access.

Thanks for all your help again! :popcorn:

---

### Post by srs5694 on 2011-01-19
Instead of wiping everything on the drive, you could try creating a Windows installation partition using Linux (fdisk/mkntfs, parted, GParted, or whatever). If you do that, Windows will be less likely to trash your Linux installation because of bugs in its partitioner.

---

### Post by avatarmonkeykirby on 2011-01-19
I'm avoiding that by installing windows first. That way I won't have to mess with partition errors or Grub.

---

### Post by avatarmonkeykirby on 2011-01-19
I'm avoiding that by installing windows first. That way I won't have to mess with partition errors or Grub. The main reason is to clear up fragment errors that are already on the Windows partition. Degraggler estimated several days to clear up the problems, but that was an underestimate. Instead of waiting several weeks to clear the defragmentation (not to mention the overly abundant windows clutter) Clean install seemed the smartest thing to do.

---

### Post by presence1960 on 2011-01-19
The main thing is you recovered your data. Compared to losing all your files reinstallation is not too hard to swallow.

---

### Post by presence1960 on 2011-01-19
The main thing is you recovered your data. Compared to losing all your files reinstallation is not too hard to swallow.

---

### Post by presence1960 on 2011-01-19
The main thing is you recovered your data. Compared to losing all your files reinstallation is not too hard to swallow.

---

