---
title: "Ubuntu Netbook (XP Wiped) and it Doesn't Work!"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by bobbystandley on 2011-01-17
Dear All,

This is my third post of this topic on the forum and so far no one has replied to me... Maybe it can't be fixed?

I installed Ubuntu Netbook (the latest version) on my brand new netbook. Chose to wipe XP and just use Ubuntu. It wiped XP and now will not boot without the USB attached, it saves nothing, it does not open half the applications and wants me to install it every time I turn it on... The install then fails and usually freezes. 

I am at a loss on what to do? I was told Ubuntu was fast and reliable...

Please anyone help? I want to like Ubuntu... 

Help me?


:KS

---

### Post by bobbystandley on 2011-01-17
```
          Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2034 MB, 2034237440 bytes
33 heads, 63 sectors/track, 1911 cylinders, total 3973120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             32     3,973,119     3,973,088   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   306,440,191   306,438,144  83 Linux
/dev/sdb2         306,442,238   312,580,095     6,137,858   5 Extended
/dev/sdb5         306,442,240   312,580,095     6,137,856  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        110F-0F3B                              vfat       PENDRIVE                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        ba9d0629-f3bd-4ae3-b7cd-aca1f69be56a   ext2                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        bd2afd75-1e6e-4f9f-96ef-45daf638fb7c   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/ba9d0629-f3bd-4ae3-b7cd-aca1f69be56a ext2       (rw,nosuid,nodev,uhelper=udisks)


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext2    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=bd2afd75-1e6e-4f9f-96ef-45daf638fb7c none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 9f 3c 00 21 0f 00 00  00 00 00 00 02 00 00 00  |..<.!...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 03 29 3b 0f 0f 11 4e  4f 20 4e 41 4d 45 20 20  |..);...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 6a 1e 00 00  66 ba 00 00 00 00 bb 00  |}.f.j...f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

I get this information.

---

### Post by bobbystandley on 2011-01-17
Begging for help!

---

### Post by Quackers on 2011-01-17
For some reason you have only one of the three boot files necessary to boot Ubuntu. You also don't have grub installed in the mbr of your hard drive.
I would suggest you follow drs305's guide below using the full chroot procedure to purge and re-install grub.
The partition you need to mount is sdb1 and the grub should be installed to sdb (NOT sdb1).

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

If you are unsure anywhere just ask. It is better to get it right now :-)

---

### Post by bobbystandley on 2011-01-17
I get to the step where I have to have an internet connection, I have one and it is on root@ubuntu...

But it is telling me there is no such file or directory when I try to download the updates...

Help?
x

---

### Post by Quackers on 2011-01-17
Please post a screenshot of the terminal screen at this time, thanks.

---

### Post by bobbystandley on 2011-01-17
There you go,

Thank you for this.
x

---

### Post by Quackers on 2011-01-17
Sorry, can you scroll up in the terminal to where you started the commands please and post another screenshot, thanks.

---

### Post by bobbystandley on 2011-01-17
I reckon I am just doomed.
x

---

### Post by Quackers on 2011-01-17
No you're not :-) Just needs some work.

---

### Post by Skull XT on 2011-01-17
pliz do you have the Ubuntu installation disc?

---

### Post by bobbystandley on 2011-01-17
Print screen, take two.
x

---

### Post by bobbystandley on 2011-01-17
Help?
x

---

### Post by Quackers on 2011-01-17
I don't see anything wrong (apart from the early error, which seems to be corrected). I think we can try it again and see if anythings is different this time. If this doesn't work I suspect that your installation may not be complete, but we'll see.
In the terminal please copy/paste these lines one at a time and press enter after each line.
```
exit
for i in /dev/pts /dev /proc /sys / ; do sudo umount /mnt/temp$i ; done
```
This should bring you back to ubuntu@ubuntu and everything unmounted, so we can start again.
```
sudo mkdir /mnt/temp 
sudo mount /dev/sdb1 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp
```
At this point we are back to where we were before.
If you now go back to the guide and try apt-get update and it fails, then I suspect your installation is not good. Maybe somebody else could comment if that proves to be the case.
Good luck :-)

---

### Post by Quackers on 2011-01-17
I've just noticed something. I have no idea whether it's significant or not, as I don't understand Linux file systems very well. I notice from the boot script that you are using ext2 as the file system type, whereas the default for the later Linux systems is ext4. It could be significant.

---

### Post by bobbystandley on 2011-01-17
Same happened again...

Anyone got any ideas?

---

### Post by Quackers on 2011-01-17
See one post up. I'll try to get some clarification.

---

### Post by drs305 on 2011-01-17
I am not sure of the problem but here are some things you can check or try. I haven't dealt with any ext2 vs ext3/4 issues but then again I don't know many users still using ext2 either.

Are you using the same version of CD (32-bit vs 64-bit) as OS? Ideally you can normally be a version or two off, but the architecture must be the same.

Have you tried it without copying resolve.conf?  Copying that file normally isn't required unless you can't connect to the Internet without it in the 'chroot' environment.

Have you tried rebooting and starting the mounting over? Sometimes things get messed up on a failed mount and it's difficult to clear things without rebooting.

Try installing an app without running the update and see if "apt-get upgrade" will work. Although the latest version would be desirable, if you can download and install the grub packages you don't *have* to update the repositories first. The chances of upgrade working when update doesn't may not be great, but it's something you can try.


I don't know if any of these will help but they are probably worth trying.

---

### Post by Quackers on 2011-01-17
Thanks drs305, I forgot about the architecture, doh!

---

