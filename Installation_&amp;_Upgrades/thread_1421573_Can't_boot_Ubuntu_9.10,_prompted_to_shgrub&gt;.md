---
title: "Can't boot Ubuntu 9.10, prompted to sh:grub&gt;"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by dobbod on 2010-03-04
I'm using Ubuntu 9.10
Dual boot with Windows XP

Hello, I don't know what happened, but suddenly, I can't boot my Ubuntu, I received grub error message during startup (I didn't really remember the error). I tried searching solution to my problem in these few days, but I can get it solved.I've tried a few tips found in this forum, but they didn't fix my problem. 

I've installed back grub with below command, but still I can't boot into Ubuntu.  I've been prompted to sh:grub> upon starting the computer.

```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

```I've also tried below steps at the prompt sh:grub>, 

```
set root=(hd0,3)
linux /vmlinuz root=/dev/sda3 ro
initrd /initrd.img
boot
```but I stucked at second line, it said "no such disk". I've also ran the bootinfoscript, and here is the result:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/core.img /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe531e531

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    41,961,779    41,961,717   7 HPFS/NTFS
/dev/sda2          41,961,780   416,549,384   374,587,605   f W95 Ext d (LBA)
/dev/sda5          41,961,843   146,818,034   104,856,192   7 HPFS/NTFS
/dev/sda6         146,818,098   251,674,289   104,856,192   7 HPFS/NTFS
/dev/sda7         251,674,353   309,652,874    57,978,522   7 HPFS/NTFS
/dev/sda8         309,652,938   311,644,934     1,991,997  82 Linux swap / Solaris
/dev/sda3         416,549,385   437,514,209    20,964,825  83 Linux
/dev/sda4         437,514,210   625,137,344   187,623,135  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x45d086da

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   943,722,359   943,722,297   7 HPFS/NTFS
/dev/sdb2         943,722,360 1,250,258,624   306,536,265   f W95 Ext d (LBA)
/dev/sdb5         943,722,423 1,250,258,624   306,536,202   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0C7C62BC7C62A066                       ntfs                                     
/dev/sda3        1751283b-b905-49fb-bc81-93e2e561bfd9   ext4       Karmic Koala                  
/dev/sda4        347190e2-ceb0-4c26-9c63-65fd94d47de5   ext4       Karmic Home                   
/dev/sda5        EEB42BEFB42BB8CB                       ntfs       Program                       
/dev/sda6        568497A4849784E1                       ntfs       Docs                          
/dev/sda7        4E4CB1184CB0FBB1                       ntfs       OS Bkp                        
/dev/sda8        cbb1f81d-2501-42e2-92d8-49b48787ab62   swap                                     
/dev/sdb1        60F84380F8435386                       ntfs       Data                          
/dev/sdb5        92DC4B11DC4AEF53                       ntfs       Backup                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda3        /mnt                     ext4       (rw)
/dev/sdb5        /media/Backup            fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda4        /media/Karmic Home       ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb1        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda7        /media/OS Bkp            fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda6        /media/Docs              fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /media/Program           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda4        /mnt                     ext4       (rw)
/dev/sda1        /media/0C7C62BC7C62A066  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3        /mnt                     ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sda3: Location of files loaded by Grub: ===================


 214.3GB: boot/grub/core.img
 214.2GB: grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  a4 81 00 00 0e 02 00 00  e6 ea 39 4b 54 e2 39 4b  |..........9KT.9K|
00000010  e6 e4 d4 43 00 00 00 00  00 00 01 00 08 00 00 00  |...C............|
00000020  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  01 00 00 00 ac b0 08 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 99 6d 32 1e  00 00 00 00 00 00 00 00  |.....m2.........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  1c 00 00 00 d8 2c ad 05  00 00 00 00 b0 1e 11 bc  |.....,..........|
00000090  54 e2 39 4b d8 2c ad 05  00 00 00 00 00 00 00 00  |T.9K.,..........|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  ff a1 00 00 18 00 00 00  b6 24 89 4b 7a ee 28 4b  |.........$.Kz.(K|
00000110  7a ee 28 4b 00 00 00 00  00 00 01 00 00 00 00 00  |z.(K............|
00000120  00 00 00 00 01 00 00 00  6c 69 62 64 6f 74 63 6f  |........libdotco|
00000130  6e 66 2d 31 2e 30 2e 73  6f 2e 30 2e 31 30 2e 34  |nf-1.0.so.0.10.4|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 74 a1 f3 57  00 00 00 00 00 00 00 00  |....t..W........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  1c 00 00 00 f4 75 e3 29  f4 75 e3 29 ac d2 e6 40  |.....u.).u.)...@|
00000190  7a ee 28 4b f4 75 e3 29  00 00 00 00 00 00 00 00  |z.(K.u.)........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200


```Kindly, please help. Thanks.

---

### Post by oldfred on 2010-03-04
Your sda3 has two copies of
/grub/core.img /boot/grub/core.img
but no other files required to boot linux, init, & fstab??

Your install of grub may have added the second core.img, did your boot files get deleted or moved to another location somehow? The boot script does not look in non-standard locations for files.

---

### Post by Axellink on 2010-03-04
I have this problem as well, but my grub folder is completely empty.  The weird thing is when i boot up via live cd, i can't mount my ubuntu hdd drive for some reason

---

### Post by dobbod on 2010-03-04
> **oldfred said:**
> Your sda3 has two copies of
/grub/core.img /boot/grub/core.img
but no other files required to boot linux, init, & fstab??

Your install of grub may have added the second core.img, did your boot files get deleted or moved to another location somehow? The boot script does not look in non-standard locations for files.
Thanks for your comment.

I remember now, maybe the files got "fixed" after I ran the command fsck in sda3. I prompted with many errors to be corrected, and press "Y" to all of them. Maybe this is the cause of the missing "other files" to boot ubuntu. Could you please guide me on how to settle this? Thanks.

---

### Post by oldfred on 2010-03-05
What we do not know is are other system files also missing so just reinstalling the boot files may not fix it. I would make sure you have backed up /home or any important files. You may need to totally reinstall.

You can chroot into your system from a liveCD and do just about anything.

Of course you must first know what partition you want to mount, in this example I'm using sda3:

sudo mount /dev/sda3 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
apt-get update
sudo apt-get update && sudo apt-get upgrade  #this updates everything
apt-get install linux-image-generic 
apt-get dist-upgrade     #would upgrade you to the latest kernel in the repositories
sudo apt-get install grub-pc  #make sure grub2 is updated  or:
sudo apt-get install --reinstall grub-pc

#When done:

exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by dobbod on 2010-03-06
I've tried the suggested commands, but most of them returned a bad result, as below. 

```
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
mount: mount point /mnt/proc does not exist
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
cp: cannot create regular file `/mnt/etc/resolv.conf': No such file or directory
ubuntu@ubuntu:~$ sudo chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
ubuntu@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory
ubuntu@ubuntu:~$ apt-get install linux-image-generic
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu@ubuntu:~$ apt-get dist-upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu@ubuntu:~$ sudo apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-pc is already the newest version.
grub-pc set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ sudo apt-get install --reinstall grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 434kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
 Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main grub-pc 1.97~beta4-1ubuntu3 [434kB]
Fetched 434kB in 19s (21.9kB/s)                                                
Preconfiguring packages ...
(Reading database ... 120319 files and directories currently installed.)
Preparing to replace grub-pc 1.97~beta4-1ubuntu3 (using .../grub-pc_1.97~beta4-1ubuntu3_i386.deb) ...
Unpacking replacement grub-pc ...
Processing triggers for man-db ...
Setting up grub-pc (1.97~beta4-1ubuntu3) ...
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

ubuntu@ubuntu:~$ 

```

I didn't ran the "sudo apt-get update && sudo apt-get upgrade" as it will take time to download the stuffs, and not really necessary as I can't get good result for the earlier commands.

If possible, I do not want to reinstall, my internet is slow and many  things I,ve done inside Ubuntu, but if it is the only way, then I will  have no choice other than reinstall.
Please advise me about those result, maybe I need to run some more  command. My root partition is sda3.

---

### Post by meierfra. on 2010-03-07
> My root partition is sda3.

/dev/sda3  seems to be missing all kinds of folders:

> mnt/dev does not exist
mount: mount point /mnt/proc does not exist


Please post the output of 

```

sudo mount /dev/sda3 /mnt
ls -l /mnt /mnt/boot

```
to see what else is missing

---

### Post by dobbod on 2010-03-08
Hi Meierfra, here is the output:

```

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
ubuntu@ubuntu:~$ ls -l /mnt /mnt/boot
/mnt:
total 12
drwxr-xr-x  3 root root 4096 2010-03-02 17:35 boot
drwxr-xr-x  2 root root 4096 2010-03-02 18:15 grub
drwx------ 21 root root 4096 2010-03-02 16:37 lost+found

/mnt/boot:
total 4
drwxr-xr-x 2 root root 4096 2010-03-04 15:36 grub
ubuntu@ubuntu:~$ 
```

Please advise what should I do next. Maybe I still can save my Ubuntu. Thanks.

---

### Post by oldfred on 2010-03-08
You do not have any of the boot files. Do you have the rest of the system. From the mnt you did do you see these directories or is entire system missing ( not the copy on the live cd):

fred@fred-laptop:/$ ls
bin    etc              initrd.img.old  lost+found  proc     srv  var
boot     lib             media       root     sys  vmlinuz
cdrom  home             lib32           mnt         sbin     tmp  vmlinuz.old
dev    initrd.img       lib64           opt         selinux  usr
fred@fred-laptop:/$

---

### Post by meierfra. on 2010-03-08
> /mnt:
total 12
drwxr-xr-x  3 root root 4096 2010-03-02 17:35 boot
drwxr-xr-x  2 root root 4096 2010-03-02 18:15 grub
drwx------ 21 root root 4096 2010-03-02 16:37 lost+found


I don't know what happened, but your whole system is gone. You only have the boot  and grub folder, which were created when you tried do reinstall grub.  Your lost+found folder seems to contain various file and folders, so in theory you might be able  recover your system. But since you have a separate home partition, I suggest to just reinstall Ubuntu. Make sure not to format /dev/sda4 during installation. Are you able to access your home partition from the LiveCD?

---

### Post by dobbod on 2010-03-09
> **meierfra. said:**
> I don't know what happened, but your whole system is gone. You only have the boot  and grub folder, which were created when you tried do reinstall grub.  You lost+found folder seems to contains various file and folders, so in theory you might be able  recover your system. But since you have a separate home partition, I suggest to just reinstall Ubuntu. Make sure not to format /dev/sda4 during installation. Are you able to access your home partition from the LiveCD?
I'm thinking the same thing now, reinstall Ubuntu seems to be a better solution for me. Yes, I can access the Home partition, and I have backed up the Home's files to other partition, in case something bad will happen during the reinstall. 

> **oldfred said:**
> You do not have any of the boot files. Do you have the rest of the system. From the mnt you did do you see these directories or is entire system missing ( not the copy on the live cd):

fred@fred-laptop:/$ ls
bin    etc              initrd.img.old  lost+found  proc     srv  var
boot     lib             media       root     sys  vmlinuz
cdrom  home             lib32           mnt         sbin     tmp  vmlinuz.old
dev    initrd.img       lib64           opt         selinux  usr
fred@fred-laptop:/$
Looks like I don't have the rest of the files/folders, compared to yours Oldfred. Only Boot, Grub and Lost+Found folders left.

I think I'll just reinstall Ubuntu now. Thanks all for helping.

---

### Post by dobbod on 2010-03-09
I've done the reinstall, everything seems okay including all files in Home folder. I can use them straight away like before. :)

Thanks all.

---

### Post by meierfra. on 2010-03-09
> I've done the reinstall, everything seems okay including all files in Home folder. 
Great, although  I would feel better if I would know what caused all your system directories to disappear.  Did you had a power outage? Anything unusual?

---

### Post by dobbod on 2010-03-10
I don't what happened meierfra, I opened Ubuntu as usual, surfed as usual, but something weird happened that day. I can see that system was reacting so slow, and I can't boot into ubuntu after I restart. I ran 'sudo fsck' through live-cd, and many things were 'fixed'. Maybe this is the reason behind the missing system directories.

---

### Post by meierfra. on 2010-03-10
.>  I can see that system was reacting so slow, and I can't boot into ubuntu after I restart. I ran 'sudo fsck' through live-cd, and many things were 'fixed'.


You should have mentioned this in your very first post.:p
fsck moves files whose paths cannot be recovered to the "lost+found" folder.  So this explains why all the system files  were missing.
Although we still don't know what corrupted your filesystem.

---

