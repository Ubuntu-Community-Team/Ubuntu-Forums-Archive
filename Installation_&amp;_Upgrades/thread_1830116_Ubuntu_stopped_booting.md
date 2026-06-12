---
title: "Ubuntu stopped booting"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by aderon on 2011-08-21
Thanks to Wubi, I had been running Ubuntu 10.04 (Wubi) inside windows-XP. A couple of days ago, however, I installed linux-image-2.6.32-34-generic binary package on my Ubuntu 10.04 (updated the kernel) and, if I remember correctly, it was working fine after the reboot. However, later that same day I left my laptop to run on battery power and it must have shut itself down after the battery runs out of power, I suppose. SInce then I have encounted the problem I haven't resolved yet. 

I can boot into Windows but when I select Ubuntu the boot loader directly goes to grup prompt. As usual I have booted with the Linux LiveCD and tried to mount the root.disk to have access to the files I am dieing to retrieve everything I have been working on for the last three months which I have not done any backup for. This time the old trick, mount -o loop, failed to get me through. The procedure and the error output are shown below.
________________________________________________
[HTML]
ubuntu@ubuntu:~$ sudo su
root@ubuntu:~# mount /dev/sda1 /mnt
root@ubuntu:~# mkdir /vdisk
root@ubuntu:~# mount -o loop /mnt/ubuntu/disks/root.disk /vdisk
mount: you must specify the filesystem type
[/HTML]Then following the error report I tried to mount with option -t and I got the following

________________________________________________________________
[HTML]
root@ubuntu:~# mount -o loop -t ext2 /mnt/ubuntu/disks/root.disk /vdisk/
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/HTML]Then with "dmesg  | tail"

__________________________________________________________________
[HTML]
root@ubuntu:~# dmesg | tail 
[ 1519.953117] sd 4:0:0:0: Attached scsi generic sg3 type 0
[ 1520.276203] sd 4:0:0:0: [sdb] 3919872 512-byte logical blocks: (2.00 GB/1.86 GiB)
[ 1520.276809] sd 4:0:0:0: [sdb] Write Protect is off
[ 1520.276814] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1520.276817] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1520.279179] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1520.279184]  sdb: sdb1
[ 1520.283306] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1520.283315] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 7921.951728] VFS: Can't find an ext2 filesystem on dev loop1.
[/HTML]Since I have never encountered such a mega-scaled disaster, I have already started to freak out. I could not find any workaround to get past this problem. The worst part of all this circumstance is that I have been preparing a beamer presentation that must be finished in a few days time. 

Hoping to find a quick help, I have visited number of web sites but I only found one suggestion menstioned on few forums saying that I have to run boot script that can be downloaded from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and then post the output in this forum. I did everything and I posted whatever written in the RESULT.txt file below:

_____________________________________________________________________
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /ntdetect.com /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk /boot/grub/core.img

sda1/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr /wubildr.mbr

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   105,855,119   105,855,057   7 NTFS / exFAT / HPFS
/dev/sda2         105,855,183   117,210,239    11,355,057   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/ramzswap0                                          swap       
/dev/sda1        CE400F5F400F4DA1                       ntfs       
/dev/sda2        4C6C-62B8                              vfat       HP_RECOVERY

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1/Wubi

00000000  80 81 e8 03 39 01 00 00  b0 9e 42 4e b1 9e 42 4e  |....9.....BN..BN|
00000010  b1 9e 42 4e 00 00 00 00  e8 03 01 00 08 00 00 00  |..BN............|
00000020  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  01 00 00 00 c8 83 5c 00  |..............\.|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 90 87 62 a2  00 00 00 00 00 00 00 00  |......b.........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  1c 00 00 00 c4 44 22 41  fc 42 0f 2e 48 98 65 e0  |.....D"A.B..H.e.|
00000090  b0 9e 42 4e 48 98 65 e0  00 00 00 00 00 00 00 00  |..BNH.e.........|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  80 81 e8 03 8d 00 00 00  ed c5 4a 4e ac 42 3e 4e  |..........JN.B>N|
00000110  ac 42 3e 4e 00 00 00 00  e8 03 01 00 08 00 00 00  |.B>N............|
00000120  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  01 00 00 00 a7 68 1f 00  |.............h..|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 4d ab 6a 15  00 00 00 00 00 00 00 00  |....M.j.........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  1c 00 00 00 40 96 3a 37  40 b1 91 32 5c 2a 29 35  |....@.:7@..2\*)5|
00000190  ac 42 3e 4e 40 b1 91 32  00 00 00 00 00 00 00 00  |.B>N@..2........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200

Unknown BootLoader on sda2

00000000  e9 a7 00 52 45 43 4f 56  45 52 59 00 02 08 20 00  |...RECOVERY... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 f0 00 cf 38 4f 06  |........?....8O.|
00000020  b0 43 ad 00 3c 2b 00 00  00 00 00 00 02 00 00 00  |.C..<+..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 b8 62 6c 4c 20  20 20 20 20 20 20 20 20  |..).blL         |
00000050  20 20 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |  FAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  c7 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 4e 54 4c 44 52 20 20  |.f..f.F..NTLDR  |
000001b0  20 20 20 20 0d 0a 4e 6f  20 53 79 73 74 65 6d 20  |    ..No System |
000001c0  44 69 73 6b 20 6f 72 0d  0a 44 69 73 6b 20 49 2f  |Disk or..Disk I/|
000001d0  4f 20 65 72 72 6f 72 0d  0a 50 72 65 73 73 20 61  |O error..Press a|
000001e0  20 6b 65 79 20 74 6f 20  72 65 73 74 61 72 74 0d  | key to restart.|
000001f0  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```Please some one out there save me from this end-of-the-world scenario. I appreaite any help!

---

### Post by Frogs Hair on 2011-08-21
See this tread , the problem may have been addressed .[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)  (WubiMega)

---

### Post by bcbc on 2011-08-21
Back up the root.disk first if you can. Then try to repair it using fsck.
```
sudo mount /dev/sda1 /mnt
sudo fsck /mnt/ubuntu/disks/root.disk
```

---

### Post by aderon on 2011-08-21
Hi bcbc,

I have done the backup already. Yes. I tried to execute the command you mentioned and this is what I found:

```

~$ sudo mount /dev/sda1 /mnt
~$ sudo fsck /win/ubuntu/disks/root.disk
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /win/ubuntu/disks/root.disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```

Does this mean that it can not be recovered?

---

### Post by bcbc on 2011-08-21
Try chkdsk /r from windows first.

---

### Post by aderon on 2011-08-22
Hi,

After running chkdsk /r on windows partition gave me funny report that I pasted hereunder:

```

C:\WINDOWS\System32> chkdsk /r
The type of the file system is NTFS.
Cannotlock current drive.

Chkdsk cannot run because the volume is in use by another process.
Would you like to schedule this volume to be checked the next time the system restarts? <Y/N> 

```


When I answer with Y/Yes it just reports that the command will run upon rebooting windows.
However, after reboot the same message I get upon execution of the  command.  Could that be some sort of virus messing with the system?

---

### Post by bcbc on 2011-08-22
That is strange. I really have no idea why that would happen. 

Usually I run chkdsk by going to (My) Computer, right clicking on the drive, Properties, Tools, Check disk for errors, Fix automatically (/f) or Scan for bad blocks (/r). Then it tells you to reboot as well. Give that a go just to rule out anything.

If that fails, you need to get a windows dvd or repair disc that you can boot to a repair prompt and run it from there.

---

### Post by bcbc on 2011-08-22
I found this link regarding your prob: [http://forum.notebookreview.com/windows-os-software/172250-scheduled-chkdsk-wont-run-reboot.html](http://forum.notebookreview.com/windows-os-software/172250-scheduled-chkdsk-wont-run-reboot.html)

Anyway - chkdsk /x does a force unmount before running /f (according to this: [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true) )

PS don't do /x this while windows is running (either schedule a normal chkdsk and change the option via msconfig or do this from a repair prompt.)

---

### Post by aderon on 2011-08-23
Hi bcbc,

After I booted the system with Win7 install CD and select the startup repair it gave displayed the following log file about the problem

```

Startup repair cannot repair this computer automatically.
.
.
Problem detail
.
.
Root Cause Found:
-------------------------
Boot Manager is missing or corrupt.
Repair action: File repair
Result: Failed. Error cide = 0 x 15
Time taken = 0 ms

```

On the other hand, the quick message that is being diplayed before ubunut bootloader jumps to grub prompt says the following:

```

Try (hd0,0): NTFS5: It is not possible to boot from the ubuntu image. The Windows partition might be corrupted. Please reboot into WIndows and run: chkdsk /r. Then try again.

```

At least things start get a little bit clearer now.

---

