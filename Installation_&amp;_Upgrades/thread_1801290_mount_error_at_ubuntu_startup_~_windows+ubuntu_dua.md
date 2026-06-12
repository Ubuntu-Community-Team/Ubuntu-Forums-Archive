---
title: "mount error at ubuntu startup ~ windows+ubuntu dual OS"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by smkengr on 2011-07-10
Hi guys,

I installed ubuntu 11.4 on windows7 (64 bit) in C:/ubuntu. Everything was working fine. I was able to work in both ubuntu and windows whenever required. Last night my laptop battery died and when I restart the system I am able to log in to windows7 but cant log into ubuntu.


On startup I am getting boot selection, I select ubuntu and then can see 
1. ubuntu, linux 2.6.38-8-generic ~ default selected
2. ubuntu in recovery mode
3. windows 7 on /dev/sda1
4. windows 7 on /dev/sda2
5. windows recovery environment on /dev/sda4


when i select the default ubuntu from grub boot loader I am getting error like 

Segmentation Fault
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found.  Try passing init= bootarg.


BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built in shell (ash)

Enter 'help' for a list of built-in commands

(initramfs)_

Now I am stuck at this point.

when I select ubuntu in recovery mode. I can mount /dev/sda2 /root and can see complete C drive. Don't know what else  I should do? I can see /root/ubuntu/disks/root.disk.



I have downloaded ubuntu live cd as well.

Any help will highly be appreciated.

many thanks

Smk

---

### Post by matt_symes on 2011-07-10
Hi

In the first instance down and run the bootinfo script in my signiture. It will give us a better picture of you hard drives. The instructions to run it are on the download page. Run it from a LiveCD / USB.

It might just be a case of running fsck, but that will give us more information.

Kind regards

---

### Post by smkengr on 2011-07-10
When I select recovery mode and do 

(initramfs) df 

Filesystem       1024-blocks   used    available   use% mounted on
none             1972492        168     1972324    0%   /dev

/dev/sda2        152006652   69829108  8217775444  46%  /host

I can see the C drive with

(initramfs) ls /hosts/


This may help to identify issue.

waiting for any reply.

---

### Post by smkengr on 2011-07-10
Thanks matt_symes.

I will paste the output shortly. I am assuming to reboot in live cd and then clicking to trial and then run this script, right?

---

### Post by matt_symes on 2011-07-10
Hi

> **smkengr said:**
> Thanks matt_symes.

I will paste the output shortly. I am assuming to reboot in live cd and then clicking to trial and then run this script, right?

Yes. That is correct. It will provide more information that supposition ever could.

Kind regards

---

### Post by smkengr on 2011-07-10
Here is the output


Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   304,422,911   304,013,312   7 NTFS / exFAT / HPFS
/dev/sda3         304,424,960   597,745,663   293,320,704   f W95 Extended (LBA)
/dev/sda5         304,427,008   597,745,663   293,318,656   7 NTFS / exFAT / HPFS
/dev/sda4         597,745,664   625,139,711    27,394,048   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2113 MB, 2113138688 bytes
127 heads, 32 sectors/track, 1015 cylinders, total 4127224 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     4,127,191     4,127,160   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7A7E72917E724643                       ntfs       SYSTEM
/dev/sda2        B6281E9A281E59A7                       ntfs       
/dev/sda4        ECAA9E4AAA9E1166                       ntfs       RECOVERY
/dev/sda5        F45C47515C470DB4                       ntfs       New Volume
/dev/sdb1        001B-9622                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/001B-9622         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 40 08 00  |.<.MSWIN4.1..@..|
00000010  02 00 04 00 00 f8 fc 00  20 00 ff 00 20 00 00 00  |........ ... ...|
00000020  b8 f9 3e 00 80 00 29 22  96 1b 00 4e 4f 20 4e 41  |..>...)"...NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200


#####################

So what next?

---

### Post by smkengr on 2011-07-10
some more outputs if that can help.

After rebooting system through ubuntu live cd


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbedb6a2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       18950   152006656    7  HPFS/NTFS
/dev/sda3           18950       37208   146660352    f  W95 Ext'd (LBA)
/dev/sda4           37208       38914    13697024    7  HPFS/NTFS
/dev/sda5           18950       37208   146659328    7  HPFS/NTFS



ubuntu@ubuntu:~$ grub
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub

ubuntu@ubuntu:~$ grub-set
grub-set-default  grub-setup        

ubuntu@ubuntu:~$ grub-setup /dev/sda1
Invalid device `/dev/sda1'.
Segmentation fault (core dumped)

ubuntu@ubuntu:~$ sudo update-grub2
/usr/sbin/grub-probe: error: cannot stat `aufs'.

ubuntu@ubuntu:~$ sudo grub-install --recheck /dev/sda
/usr/sbin/grub-probe: error: cannot stat `aufs'.
ubuntu@ubuntu:~$ sudo update-grub2
/usr/sbin/grub-probe: error: cannot stat `aufs'.

ubuntu@ubuntu:~$ sudo fsck -fyc /dev/sda1
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1

ubuntu@ubuntu:~$ sudo fsck -fyc /dev/sda#
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: No such file or directory while trying to open /dev/sda#
Possibly non-existent device?



Any idea?

I have important documents on ubuntu's user home drive. can i save that data? I believe this problem should not force me to reinstall ubuntu on windows? Waiting for any help

---

### Post by matt_symes on 2011-07-10
Hi

You have a Wubi install and that is a pain because i have no experience with Wubi.
> 
File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

That is the problem with the disc. The filesystem is corrupted, hence the reason you cannot boot into it.

I would suggest mounting the partition and performing an fsck check on the root disk (not mounting the root disc itself), however i am not sure if this is the best course of action in this case.

I will call for the calvary to get an opnion from someone who knows Wubi much better than i do.

Kind regards

---

### Post by smkengr on 2011-07-10
ok thanks for answering.

Can we save data from /home/user ??

---

### Post by Rubi1200 on 2011-07-10
Hi smkengr,

Matt asked me to take a look at this thread and offer some help.

I want to start by pointing out that you should not run commands blindly without asking us here what effect they will have.

I am not referring to the commands Matt asked you to run, but those you decided to do yourself.

Wubi installs cannot be booted from the MBR using GRUB, so attempting to install GRUB will lead to Windows also not being able to boot in such a situation.

Also, running fsck without knowing which partition to run it on is likewise inadvisable.

To try and fix this, boot from the LiveCD in trial mode and run the following commands:

```
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo e2fsck -f -y -v /media/win/ubuntu/disks/root.disk
```

After the last command completes, mount the root.disk to access your files:

```
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```

Now you can reboot, taking out the CD, and hopefully be back in Ubuntu.

---

### Post by smkengr on 2011-07-10
Good news is I have saved my data but still thinking to recover it rather than reinstalling ubuntu on windows.

I used the following to recover the data 

sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

could see all the data in /mnt/home/

now i have /mnt/boot as well anyone will recommend something to recover both OS ubuntu+windows7. I am using ubuntu wubi 11.4.

Cheers

---

### Post by smkengr on 2011-07-10
Hi Rubi1200, 
Just checked your reply mate, thanks alot. 
My system is back. please mark this thread as solved.

Cheers

---

### Post by Rubi1200 on 2011-07-10
Okay, that is great news and I am glad things worked out for you :-)

You need to mark this Solved by using the Thread Tools near the top of the page.

Enjoy!

(As a general precaution make a backup copy of the root.disk to somewhere safe like an external medium; you never know when you may need it)

---

