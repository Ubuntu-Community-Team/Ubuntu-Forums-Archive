---
title: "Dual Boot Problem -- error: unknown filesystem grub rescue&gt;"
date: 2011-12-02
forum: Installation &amp; Upgrades
---

### Post by lingben on 2011-12-02
I had a dual boot system on a laptop with lubuntu and XP.

  I wanted to remove lubuntu and replace it with linux mint. So I  booted into the linux mint live CD and went through the first few steps  of the install. I chose to erase lubuntu and install linux mint on top  of it. After a few steps and in the middle of the install for no  apparent reason the laptop's power went out!

  Restarted and went into the live CD again but this time the menu for  the install was different. Instead of offering me the choice of  installing over lubuntu and keeping XP it offered me the choice of  adding linux mint to the mix (I don't want to erase my XP install or  documents).

  At this point I wanted to just uninstall lubuntu so I quit the linux  mint installation and restarted to go into windows and erase the lubuntu  partition from there.
  

But I was met with:
```

error: unknown filesystem 

grub rescue>

```woah! 


My goal is to remove the linux distros. Either by booting into windows XP and removing the partitions from there or by loading a live CD of linux mint and removing the now unnecessary partitions that are there as a result of the previous lubuntu install and the unsuccessful linux mint install.


Unfortunately I don't have a windows XP repair/recovery disk.


Here's what I see in the partitions menu of the installation process:

Device         Type       Mount point Format? Size   Used

/dev/sda
  /dev/sda1   ntfs                                        _______________54352 MB  unknown
  /dev/sda6   ext4 _______________                                     21400 MB  5309 MB
  /dev/sda7   swap                                     _______________2130 MB    0 MB 
  /dev/sda5   swap                                     _______________2135 MB    0 MB


there is a pull down menu "Device for boot loader installation:"

/dev/sda ATA Hitachi HTSS4258 (80 GB)
/dev/sda1 Microsoft Windows XP Home Edition
/dev/sda6 Linux Mint 11 LXDE (11)


Would appreciate any and all help. Thank you in advance!

---

### Post by Rubi1200 on 2011-12-02
Hi and welcome to the forums :)

Please boot the computer with the LiveCD in live mode and post the results of the boot info script.

There is a link at the bottom of my post with instructions.

---

### Post by lingben on 2011-12-02
thanks, I've downloaded and extracted the folder and finally figured out how to do it! 
```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Mounting failed:   $MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 11 LXDE
    Boot files:        /etc/fstab

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   106,156,820   106,156,758   7 NTFS / exFAT / HPFS
/dev/sda2         106,158,078   156,301,311    50,143,234   5 Extended
/dev/sda5         152,129,536   156,301,311     4,171,776  82 Linux swap / Solaris
/dev/sda6         106,158,080   147,955,711    41,797,632  83 Linux
/dev/sda7         147,957,760   152,119,295     4,161,536  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        FE14279314274E49                       ntfs       
/dev/sda5        25e6ce85-2765-4c1a-a8b0-4551aee367fb   swap       
/dev/sda6        370a0dcf-03f5-4342-975a-6f3b35a73ea6   ext4       
/dev/sda7        3e37e3fd-2c94-49c6-8671-c0bd632cfd46   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/370a0dcf-03f5-4342-975a-6f3b35a73ea6 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=3e37e3fd-2c94-49c6-8671-c0bd632cfd46 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  50.768554688 = 54.512320512   boot/initrd.img-2.6.38-8-generic               2
  64.752418518 = 69.527379968   boot/vmlinuz-2.6.38-8-generic                  1
  50.768554688 = 54.512320512   initrd.img                                     2
  64.752418518 = 69.527379968   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  69 1a 81 ab 0c 72 03 38  48 00 06 91 3c 39 2b 14  |i....r.8H...<9+.|
00000010  b7 9e 0e 08 75 ba be 07  83 29 60 90 91 60 07 af  |....u....)`..`..|
00000020  4f de 4e 7d c3 c0 85 fb  85 a9 5c 5e f7 ef c2 c2  |O.N}......\^....|
00000030  43 00 22 80 f3 00 2f c5  89 ca 8b 43 df 1b c2 7c  |C.".../....C...||
00000040  fb 10 3a 64 9e 9d 2f 14  ee ba 47 35 0b 9d ad 55  |..:d../...G5...U|
00000050  00 a5 58 89 b4 c1 a5 1b  91 92 b3 24 ba d1 dd c7  |..X........$....|
00000060  f0 53 e6 91 3c 39 2b 14  b7 9e 0e 08 75 ba be 07  |.S..<9+.....u...|
00000070  81 80 1d 07 0b 77 b8 d7  14 40 4b 70 43 07 09 f5  |.....w...@KpC...|
00000080  65 c2 02 08 40 41 f9 61  28 3e cf 5f 3e 7b 5d ff  |e...@A.a(>._>{].|
00000090  68 7f 5a e3 ea d4 e1 c2  74 a7 85 2a 4f d3 a5 52  |h.Z.....t..*O..R|
000000a0  fb 54 37 cb 9f a5 7c fd  d2 65 34 9f 53 54 e6 c2  |.T7...|..e4.ST..|
000000b0  0c ea 9d 3d 7e 86 13 e8  4f 63 d3 4a f9 fa 5e 1f  |...=~...Oc.J..^.|
000000c0  d6 b8 fb e7 c4 30 95 3e  4b 9d ec 2a 4f df 26 74  |.....0.>K..*O.&t|
000000d0  f6 1a a4 cf a9 25 7d 49  f5 27 d4 9d 90 e6 f6 dc  |.....%}I.'......|
000000e0  da 6a 9f 29 7d 0d 4b e8  04 29 52 a4 fb cb 7a 63  |.j.)}.K..)R...zc|
000000f0  06 0c 80 59 0f 15 8a cf  3f 22 31 95 cf b3 d9 7e  |...Y....?"1....~|
00000100  87 df be bc 81 fb b4 11  d0 20 8e 9b 06 a6 ec f0  |......... ......|
00000110  8f a8 01 fe 01 20 01 f0  b5 8e 3e 0d ae 8c 5e 8a  |..... ....>...^.|
00000120  d7 29 50 0f 46 32 a9 65  05 38 c8 0d a5 9a 60 a8  |.)P.F2.e.8....`.|
00000130  83 19 06 48 81 8e 4c da  5b 36 38 b1 19 c1 88 20  |...H..L.[68.... |
00000140  57 41 ca 57 a0 6b b1 33  c0 12 65 90 f1 58 ac f3  |WA.W.k.3..e..X..|
00000150  f2 23 19 5c fb 3d 80 da  60 00 02 a6 81 7c e4 04  |.#.\.=..`....|..|
00000160  4d 48 d2 9a 3e 70 f7 90  48 e2 5c 6e f1 17 61 2c  |MH..>p..H.\n..a,|
00000170  c8 1d a7 7b 21 b8 67 ee  77 aa 9b 9b 77 7b 06 00  |...{!.g.w...w{..|
00000180  9d 2d e8 af be 73 05 b8  3b a0 5d 88 48 76 b9 02  |.-...s..;.].Hv..|
00000190  29 90 06 9c 8c 6e cd cd  22 f6 86 8a 14 74 61 6b  |)....n.."....tak|
000001a0  59 f2 da 77 7b b7 77 18  5a 92 ef 41 da f7 af 14  |Y..w{.w.Z..A....|
000001b0  08 a0 2a 68 17 ce 40 44  d4 8d 29 a3 e7 00 00 fe  |..*h..@D..).....|
000001c0  ff ff 82 fe ff ff 02 78  bd 02 00 a8 3f 00 00 fe  |.......x....?...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 c8 7d 02 00 00  |............}...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by drs305 on 2011-12-02
I initially started to tell you how to restore Ubuntu, but that isn't what you want and may not work since the installation was aborted. 

I'll have to let a Windows user help you restore your sda1 partition to a usable condition. Using an XP repair CD would be the way to do it, but as you said you don't have one available.

---

### Post by lingben on 2011-12-02
sorry but what/where is the GRUB menu? I'm a little over my head here so please bear with me.

Here's a screenshot of gparted if it helps:

[http://i.imgur.com/HMleo.png](http://i.imgur.com/HMleo.png)

my ultimate goal is to remove all installed linux **so that** I can then install linux mint alongside XP

I don't want to touch the XP install because it has all documents, files, etc. that I need so if there is a way to install on top of the existing linux OS' already there that's fine, the problem is that the live CD no longer gives me that option as it did before.

now, it gives me three options, to add linux mint to the OS'es I have, to remove everything and install linux mint instead of all, or the third, to "fine tune" the partitions myself, which is the menu I quoted above.

hope that helps to clarify things

---

### Post by drs305 on 2011-12-02
> **lingben said:**
> sorry but what/where is the GRUB menu? I'm a little over my head here so please bear with me.

Here's a screenshot of gparted if it helps:

[http://i.imgur.com/HMleo.png](http://i.imgur.com/HMleo.png)

I revised my post when I saw you really weren't interested in restoring Ubuntu. Windows is not my area of expertise so you'll have to await further input by other helpers.  Best of luck.

---

### Post by lingben on 2011-12-02
actually restoring ubuntu/lubuntu would be fine, is that what's wrong?

once I do that, then I can install linux mint in its place

right?

---

### Post by drs305 on 2011-12-02
> **lingben said:**
> actually restoring ubuntu/lubuntu would be fine, is that what's wrong?

once I do that, then I can install linux mint in its place

right?

Your Ubuntu installation most likely did not survive the interruption, but you can try the following to see if it will boot:

We'll use a quick method which might work if the first command returns a long list of *.mod files. If not, we will have to do a more comprehensive repair.

From the Grub rescue prompt:
```

ls (hd0,6)/boot/grub # If you don't see the module files, stop and let us know
set prefix=(hd0,6)/boot/grub
set root=(hd0,6)
insmod (hd0,6)/boot/grub/linux.mod
linux (hd0,6)/vmlinuz root=/dev/sda6
initrd (hd0,6)/initrd.img
boot

```
If it boots:
```

sudo grub-install /dev/sda
sudo update-grub

```

---

### Post by Newbeatontheblock on 2011-12-02
Hello have you tried booting to your XP  with a Hirens Boot CD ?  Just set your pc to boot from dvd/cdrom then boot into the Harddrive choose Windows and then copy and past all your data onto an external harddrive.....
IF your XP installlation has all kinds of paid apps use tools like productkey to recover all your productkeys 
[http://www.nirsoft.net/utils/product_cd_key_viewer.html](http://www.nirsoft.net/utils/product_cd_key_viewer.html)
After that kick windows and Boot Ubuntu from usb or cd rom and then install your favourite Linux  and setup XP in VM ware... Or setup a dualboot again

Dunno if this helps  you out really cause i m a newby if it comes to linux 

and i would really advice you to follow tips from all others above mine 

but i got the same thing going on a few months ago after dualbooting and experimenting and this is how i fixed it... All the best

---

### Post by lingben on 2011-12-02
at

```
grub rescue>
```

I entered:

```
ls (hd0,6)/boot/grub
```

it gave me

```
./ ../ gfxblacklist.txt grubenv linuxmint.png
```

---

### Post by drs305 on 2011-12-02
As feared, your Grub folder contents have been removed, as have probably many of your other system files.

To be honest, unless you have data on the partition, it would probably be quicker to do a full install from a LiveCD than try to repair a damaged system. 

You could try to install Grub by chrooting into your Ubuntu partition but it's only going to work if your other system files are intact. If you want to try it, click the "Chroot" link in my signature line. The partition to chroot into would be sda6.

---

### Post by lingben on 2011-12-03
> **drs305 said:**
> As feared, your Grub folder contents have been removed, as have probably many of your other system files.

this must have happened during the interrupted install process. by 'other system files' you're referring to the linux partition and not the windows partition, I hope...


> **drs305 said:**
> To be honest, unless you have data on the partition, it would probably be quicker to do a full install from a LiveCD than try to repair a damaged system.
 
which partition are you referring to? if to the linux partition, no, I do not have any data there. what do you mean by "full install"? do you mean as a replacement of the existing linux OS'es there now?


if you're referring to the windows partition, yes, I do have data there and want to keep it



> **drs305 said:**
> You could try to install Grub by chrooting into your Ubuntu partition but it's only going to work if your other system files are intact. If you want to try it, click the "Chroot" link in my signature line. The partition to chroot into would be sda6.

please slow down, I don't understand that at all. can you explain it with more details?


thank you

---

### Post by drs305 on 2011-12-03
Everything I discussed should apply only to the Linux partition. Ubuntu does not alter another partition unless you specifically take action to do so (such as allowing the installation to take space from another partition for installing Ubuntu). Ubuntu/Grub may also overwrite the MBR, but otherwise should not affect your Windows or other partitions.

By 'full installation', I meant accomplishing a complete, new installation on the existing Ubuntu partition. You would select 'Something else' during the installation, tell the installer to use the existing Ubuntu partition, and designate that partition as the mountpoint (/).

I didn't discuss 'Chroot' because it is all spelled out in the link I provided. You can use the 'chroot' procedure to try to repair an existing system. Normally, when you run commands in a LiveCD environment, the commands only act on the LiveCD files. 

By 'chrooting', you can make the commands act as if you were actually running your real installation, and the commands apply to that installation's files rather than those of the CD.

In your case, I would probably recommend a new, fresh installation. But if you want to try 'chrooting' to see if you can recover your current Ubuntu installation by repairing Grub the procedures are detailed in the link.

---

### Post by lingben on 2011-12-04
Thanks.

I attempted to install linux mint (LXDE v11) along side all existing OS'es (windows and previous linux) once more but the power cut out again - this while the laptop is connected to a power source!!

I tried again and it happened again.

Each time a partition is partially created which leaves less and less space for the next install attempt.

I think something is wrong with the laptop, wiring or something for it to cut out like that. I don't think it is overheating since it has ample space for airflow (I've got it jacked up on "stilts" for max airflow).

At this point I'll try to fix it via windows and then once I'm in windows remove the linux partitions and attempt again from a live CD.

Thank you for your help.

---

### Post by oldfred on 2011-12-05
Boot script showed this:
> 
    Mounting failed:   $MFTMirr does not match $MFT (record 1).

That says you need to run chkdsk from your XP disk. If you do not have one, you can run chkdsk from any Windows repairCD. A Windows 7 disk will not autorepair a XP system, but can run chkdsk and restore a XP style partition boot sector. (I have done that.)

Then if chkdsk fails:
If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

If you know someone with Windows 7.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by marinara on 2011-12-05
> **lingben said:**
> Thanks.


I tried again and it happened again.

Each time a partition is partially created which leaves less and less space for the next install attempt.

I think something is wrong with the laptop, wiring or something for it to cut out like that. I don't think it is overheating since it has ample space for airflow (I've got it jacked up on "stilts" for max airflow).

At this point I'll try to fix it via windows and then once I'm in windows remove the linux partitions and attempt again from a live CD.

Thank you for your help.

my 2 cents.  
It's not unusual for PCs to reset or power off during hardware detection.  IIRC, windows 98 used to reboot once during installation just for that reason.

so, the problem is with linux mint, it doesn't like your laptop.

---

