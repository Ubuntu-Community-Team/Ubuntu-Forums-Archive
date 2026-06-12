---
title: "Grub and Windows 7 (you've seen this before, but this is unique)"
date: 2011-06-25
forum: Installation &amp; Upgrades
---

### Post by dmeppley on 2011-06-25
I recently installed Windows 7 while having Ubuntu 11.04 installed, meaning my GRUB was now gone.
My Ubuntu had taken up the entired harddrive, but I freed up space for Windows.
After trying Ubuntu from my USB, I attempted to mount my Linux partition and recover GRUB.
It said the installation was successful, but now when I restart my computer, a black screen comes up.  I only have access to Ubuntu via my flash drive, which I'm currently using to use the internet with.
I had most of my stuff backed up before I went into Windows 7, but I would really like to recover my old Ubuntu profile and have everything the way it was before.

---

### Post by YesWeCan on 2011-06-25
Hi. Would you download this and post RESULTS.txt please?
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by dmeppley on 2011-06-25
```
pre { font-family: "Liberation Serif"; }p { margin-bottom: 0.08in; }                    Boot Info Script 0.60    from 17 May

 2011   ============================= Boot Info Summary: ===============================   => 

Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector      1 of the same hard drive for 

core.img. core.img is at this location and      looks in partition 1 for /boot/grub.  => Syslinux MBR (3.61-4.03) 

is installed in the MBR of /dev/sdb.  sda1: 

__________________________________________________________________________      File system:       

ext4     Boot sector type:  -     Boot sector info:       Operating System:       Boot files:          sda2: 

__________________________________________________________________________      File system:       

ntfs     Boot sector type:  Windows Vista/7     Boot sector info:   No errors found in the Boot Parameter Block.     

Operating System:       Boot files:        /bootmgr /Boot/BCD  sda3: 

__________________________________________________________________________      File system:       

ntfs     Boot sector type:  Windows Vista/7     Boot sector info:   No errors found in the Boot Parameter Block.     

Operating System:  Windows 7     Boot files:        /Windows/System32/winload.exe  sda4: 

__________________________________________________________________________      File system:       

Extended Partition     Boot sector type:  Unknown     Boot sector info:    sda5: 

__________________________________________________________________________      File system:       

swap     Boot sector type:  -     Boot sector info:    sdb1: 

__________________________________________________________________________      File system:       

vfat     Boot sector type:  SYSLINUX 3.86 2010-04-01     Boot sector info:   Syslinux looks at sector 65540 of 

/dev/sdb1 for its                         second stage. No errors found in the Boot Parameter                         Block.     Operating System:       Boot 

files:        /syslinux/syslinux.cfg /ldlinux.sys  ============================ Drive/Partition Info: 

=============================  Drive: sda 

_____________________________________________________________________  Disk /dev/sda: 

320.1 GB, 320072933376 bytes 255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors 

Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  

Start Sector    End Sector  # of Sectors  Id System  /dev/sda1               2,048   575,164,415   575,162,368  83 Linux 

/dev/sda2    *    575,164,416   575,369,215       204,800   7 NTFS / exFAT / HPFS /dev/sda3         575,369,216   

602,898,431    27,529,216   7 NTFS / exFAT / HPFS /dev/sda4         602,900,478   625,141,759    22,241,282   5 

Extended /dev/sda5         602,900,480   625,141,759    22,241,280  82 Linux swap / Solaris   Drive: sdb 

_____________________________________________________________________  Disk /dev/sdb: 


8036 MB, 8036285952 bytes 248 heads, 62 sectors/track, 1020 cylinders, total 15695871 sectors Units 

= sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start 

Sector    End Sector  # of Sectors  Id System  /dev/sdb1    *             62    15,683,519    15,683,458   b W95 FAT32   "blkid" 

output: ________________________________________________________________  Device           UUID                                   

TYPE       LABEL  /dev/loop0                                              squashfs    /dev/sda1        740c8873-1ecf-4b44-b5aa-5db45c058e88   ext4        /dev/sda2        

04647E1D647E1222                       ntfs       System Reserved /dev/sda3        06D8811AD881095F                       ntfs        /dev/sda5        

317db2a2-2e8b-4b85-a631-05dfffb202b5   swap        /dev/sdb1        BA2A-ACD1                              vfat       PENDRIVE  

================================ Mount points: =================================  Device           

Mount_Point              Type       Options  /dev/loop0       /rofs                    squashfs   (ro,noatime) /dev/sda1        /media/740c8873-1ecf-

4b44-b5aa-5db45c058e88 ext4       (rw,nosuid,nodev,uhelper=udisks) /dev/sda1        /media/sda1              ext4       (rw) 

/dev/sdb1        /cdrom                   vfat       

(rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro) 

/dev/sr1         /media/U3 System         iso9660    

(ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)   

========================= sdb1/syslinux/syslinux.cfg: ==========================  

-------------------------------------------------------------------------------- include menu.cfg default 

vesamenu.c32 prompt 0 timeout 50 gfxboot bootlogo 

--------------------------------------------------------------------------------  ================= sdb1: Location 

of files loaded by Syslinux: ==================             GiB - GB             File                                 Fragment(s)              ?? = ??             ldlinux.sys                                    1             ?? = 

??             syslinux/syslinux.cfg                          1             ?? = ??             syslinux/vesamenu.c32                          1  ============== sdb1: Version of 

COM32(R) files used by Syslinux: ===============   syslinux/vesamenu.c32              :  COM32R module (v3.xx)  

======================== Unknown MBRs/Boot Sectors/etc: ========================  

Unknown BootLoader on sda4  00000000  b4 8c 4e ff cc 9f 59 ff  db ab 60 ff e1 b0 62 ff  |..N...Y...`...b.| 

00000010  e2 b0 63 ff e3 b1 63 ff  e3 b1 63 ff e3 b1 63 ff  |..c...c...c...c.| 00000020  e3 b1 63 ff e3 b1 63 ff  e3 

b1 63 ff e3 b1 63 ff  |..c...c...c...c.| * 00000040  e3 b1 63 ff e3 b1 63 ff  ef d4 a8 ff a1 68 0d fc  |..c...c......h..| 

00000050  9f 60 00 08 ff ff ff 00  ff ff ff 00 ff ff ff 00  |.`..............| 00000060  ff ff ff 00 ff ff ff 00  ff ff ff 00 ff ff ff 00  

|................| * 00000080  ff ff ff 00 ff ff ff 00  9f 60 00 08 a1 68 0d fc  |.........`...h..| 00000090  ef d4 a8 ff e2 b0 

63 ff  e1 b0 62 ff dd ac 60 ff  |......c...b...`.| 000000a0  d4 a5 5c ff c1 97 54 ff  a6 82 49 ff b0 62 48 ff  

|..\...T...I..bH.| 000000b0  cd 73 4d ff ce 7c 3f ff  c8 54 53 ff ca 66 42 ff  |.sM..|?..TS..fB.| 000000c0  b8 50 3a 

ff b2 24 35 ff  9f 37 30 ff 98 25 30 ff  |.P:..$5..70..%0.| 000000d0  a5 78 46 ff c3 98 55 ff  d7 a7 5e ff df ae 61 

ff  |.xF...U...^...a.| 000000e0  e2 b0 63 ff e3 b1 63 ff  e3 b1 63 ff e3 b1 63 ff  |..c...c...c...c.| 000000f0  e3 b1 

63 ff e3 b1 63 ff  e3 b1 63 ff e3 b1 63 ff  |..c...c...c...c.| 00000100  e3 b1 63 ff e3 b1 63 ff  ef d4 a8 ff a1 68 0d 

fc  |..c...c......h..| 00000110  9f 60 00 08 ff ff ff 00  ff ff ff 00 ff ff ff 00  |.`..............| 00000120  ff ff ff 00 ff ff ff 00  

ff ff ff 00 ff ff ff 00  |................| * 00000140  ff ff ff 00 ff ff ff 00  9f 60 00 08 a1 68 0d fc  |.........`...h..| 00000150  

ef d4 a8 ff e3 b1 63 ff  e3 b1 63 ff e3 b1 63 ff  |......c...c...c.| 00000160  e3 b1 63 ff e3 b1 63 ff  e2 b0 63 ff df 

ae 61 ff  |..c...c...c...a.| 00000170  d8 a9 5e ff ca 9e 58 ff  b2 8d 4a ff c4 a8 40 ff  |..^...X...J...@.| 00000180  

fd ef 7e ff fd ef 7e ff  fd ef 7e ff fd ef 7e ff  |..~...~...~...~.| 00000190  fd ef 7e ff fd ef 7e ff  fd ef 7e ff fb ed 7c ff  

|..~...~...~...|.| 000001a0  ba 9b 36 ff b4 8c 4e ff  cc 9f 59 ff da aa 5f ff  |..6...N...Y..._.| 000001b0  df ae 61 ff 

e2 b0 63 ff  e3 b1 63 ff e3 b1 00 fe  |..a...c...c.....| 000001c0  ff ff 82 fe ff ff 02 00  00 00 00 60 53 01 00 00  

|...........`S...| 000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................| * 000001f0  00 00 00 

00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.| 00000200   =============================== 

StdErr Messages: ===============================  /home/ubuntu/Desktop/boot_info_script.sh: line 

2457: cd: /media/740c8873-1ecf-4b44-b5aa-5db45c058e88 /media/sda1/: No such file or 

directory
```

---

### Post by YesWeCan on 2011-06-25
Oh - that's impossible to read. I should have mentioned to put it inside code tags. You can edit your post, highlight the text and click on the # button to put ```

``` around it.
I think it needs a load of carriage returns too. Perhaps you could try recopying it.

I've weeded the summary:
```
Boot Info Script 0.60 from 17 May 2011
============================= Boot Info Summary: ===============================
=> Grub2 (v1.97-1.9 is installed in the MBR of /dev/sda and looks at sector 1 of
 the same hard drive for core.img. core.img is at this location and looks in 
partition 1 for /boot/grub. 
=> Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb. 

sda1: __________________________________________________ ________________________ 
File system: ext4 Boot sector type: - 
Boot sector info: Operating System: 
Boot files: 

sda2: __________________________________________________ ________________________ 
File system: ntfs Boot sector type: Windows Vista/7 
Boot sector info: 
No errors found in the Boot Parameter Block. 
Operating System: Boot files: /bootmgr /Boot/BCD 

sda3: __________________________________________________ ________________________ 
File system: ntfs 
Boot sector type: Windows Vista/7 
Boot sector info: No errors found in the Boot Parameter Block. 
Operating System: Windows 7 
Boot files: /Windows/System32/winload.exe 

sda4: __________________________________________________ ________________________ 
File system: Extended Partition 
Boot sector type: Unknown 
Boot sector info: 

sda5: __________________________________________________ ________________________ 
File system: swap 
Boot sector type: - 
Boot sector info: 

sdb1: __________________________________________________ ________________________ 
File system: vfat 
Boot sector type: SYSLINUX 3.86 2010-04-01 
Boot sector info: Syslinux looks at sector 65540 of /dev/sdb1 for its second stage. 
No errors found in the Boot Parameter Block. 
Operating System: 
Boot files: /syslinux/syslinux.cfg /ldlinux.sys 
```

```
============================ Drive/Partition Info: ============================= 

Drive: 
sda __________________________________________________ ___________________ 
Disk /dev/sda: 320.1 GB, 320072933376 bytes 255 heads, 
63 sectors/track, 38913 cylinders, total 625142448 sectors Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition Boot   Start Sector  End Sector     # of Sectors   Id   System 
/dev/sda1        2,048         575,164,415    575,162,368    83   Linux 
/dev/sda2  *     575,164,416   575,369,215    204,800         7   NTFS / exFAT / HPFS 
/dev/sda3        575,369,216   602,898,431    27,529,216      7   NTFS / exFAT / HPFS 
/dev/sda4        602,900,478   625,141,759    22,241,282      5   Extended 
/dev/sda5        602,900,480   625,141,759    22,241,280     82   Linux swap / Solaris Drive: 

sdb __________________________________________________ ___________________ 
Disk /dev/sdb: 8036 MB, 8036285952 bytes 248 heads, 
62 sectors/track, 1020 cylinders, total 15695871 sectors Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 

Partition Boot Start Sector End Sector # of Sectors Id System 
/dev/sdb1 * 62 15,683,519 15,683,458 b W95 FAT32 


"blkid" output: 
__________________________________________________ ______________ 
Device      UUID                                   TYPE       LABEL 
/dev/loop0                                         squashfs 
/dev/sda1   740c8873-1ecf-4b44-b5aa-5db45c058e88   ext4 
/dev/sda2   04647E1D647E1222                       ntfs       System Reserved 
/dev/sda3   06D8811AD881095F                       ntfs 
/dev/sda5   317db2a2-2e8b-4b85-a631-05dfffb202b5   swap 
/dev/sdb1   BA2A-ACD1                              vfat       PENDRIVE 

```

---

### Post by YesWeCan on 2011-06-25
> **dmeppley said:**
> My Ubuntu had taken up the entired harddrive, but I freed up space for Windows.
What method did you use to shrink the Ubuntu partition?

---

### Post by dmeppley on 2011-06-25
Gparted.  I basically just gave Windows about 15gbs or so to install.  That's all I needed it for.

---

### Post by YesWeCan on 2011-06-25
GParted should have done a good job. I would like to know what is going on with sda1, your Ubuntu partition. The bootinfoscript doesn't see your /boot directory there.

If you run Ubuntu in USB, would you mount sda1 and have a look at it...does the filesystem look ok? Does it have a /boot/grub directory with a grub.cfg and loads of other files in it?
[COLOR=Navy]sudo mount /dev/sda1 /mnt
cd /mnt
ls[/COLOR]
etc

It would also be prudent to run a filesystem check on that partition BEFORE YOU MOUNT IT: Don't run the check while it is mounted.
[COLOR=Navy]sudo e2fsck -fv /dev/sda1[/COLOR]

Worst case you may need to reinstall Ubuntu into sda1 and grub into sda. Let's see if that is necessary first.

---

### Post by dmeppley on 2011-06-25
It says I'm already mounted, or it's busy.

---

### Post by Quackers on 2011-06-26
> **dmeppley said:**
> It says I'm already mounted, or it's busy.

Try and run the check from a live cd desktop.

---

### Post by dmeppley on 2011-06-26
I'm horribly sick at the moment.  Thanks for all the support, I'll reply on this thread tomorrow when I'm better, I hope.

---

### Post by dmeppley on 2011-07-27
I'm back, if anyone can help that'd be appreciated.

---

### Post by oldfred on 2011-07-27
Did you run the fsck as recommended in Post #7 by        YesWeCan?

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors:
sudo e2fsck -f -y -v /dev/sda1

Try this, is sure swapoff completed:
root@ubuntu# fuser -vam /dev/sda1
root@ubuntu# lsof /dev/sda1
Terminate with "kill [pid]" or "kill -9 [pid]

If not:
Problem running e2fsck apparently in use by the system,  Use Slitaz
[http://ubuntuforums.org/showthread.php?t=1713946](http://ubuntuforums.org/showthread.php?t=1713946)
SATA will use sda1 and IDE devices use hda1 in Slitaz

---

### Post by dmeppley on 2011-07-27
I'm running off of a live usb, can I still do that?

---

### Post by ddastoor on 2011-07-27
let's say win7 was installed on /dev/sda1, and ubuntu on /dev/sda2
when u installed grub, did u install it on /dev/sda or /dev/sda1 or 2 ?
u should install grub back on /dev/sda (MBR) i believe...

---

### Post by dmeppley on 2011-07-27
I think it's sda1.
how do I check again?
sorry I've been sick and I forgot.

---

### Post by ddastoor on 2011-07-28
Hope you feel better. This may be the problem. Whenever you boot off a hard drive, the bios loads, in a nutshell, starts loading the OS from the HDD's MBR (master boot record), so when you install grub, this would be on /dev/sda NOT sda1, 2 etc.. 

sda[n] are the various partitions that created, so :

MBR for booting on 1st HDD: /dev/sda
1st partiton on 1st HDD: /dev/sda1
2nd partiton on 1st HDD: /dev/sda2
and so on.. 

MBR for booting on (say external USB HDD) /dev/sdb
1st partiton USB HDD: /dev/sdb1
2nd partiton USB HDD: /dev/sdb2
and so on.. 

point is: if u want to boot off any HDD, u should install grub in the MBR of that HDD (without the number)


You can check the grub.cfg (should be withen /boot/grub) to see where it's pointing to.

If you do realize that this is the case, then either install grub manually, once in ubuntu:
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html]("http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html")

or boot off the Live Ubuntu CD and then reinsall GRUB in the correct location.

p.s. 
if u care at this point:
You can install any bootloader into sda[n] for loading OSs but then u'll have to install another bootloader into the MBR (say /dev/sda) anyway to then "chainload" into the sda[n] boot loader ..

---

