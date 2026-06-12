---
title: "Grub Rescue after attempted dualboot install (Somewhat green user)"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by serkit_ant on 2010-11-17
I have dabbled with ubuntu before and I somewhat know my way around a computer pretty well. I am not new to dual booting, as I have done it before. I am however new to the concept of working with netbooks or laptops in general and don't really know Linux too well. Until now, I have only dealt with desktops. 

I recently received an Asus Eee PC 1005HAB netbook loaded with Win XP Home with a 160gig Hd. I decided to get back into playing around with Linux and decided to put EasyPeasy distro onto a 2gig SD card with Unetbootin. After deciding that I liked the distro, I went abouts installing it as a second OS in a new partition because I don't want to lose what I have in XP (itunes, photos, ect.) Installation went without a hitch, and I was able to boot up EasyPeasy once from the harddrive after reboot from installation. Anytime after that I would get error: no such partition grub rescue>. 

After searching the forums and finding that I am not the only one with this error after an install, I tried to find out what I could do about it. Since I didn't find anyone with the same exact problem, I decided to join the forums and ask about my own specifics. 

I think the problem is some kind of boot problem with the partitions and something to do with the bootloader. If it wasn't for the live SD card, I wouldn't have any kind of OS to work with. I ran the boot_info_script55.sh in terminal and this is what I got:

>                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,052,174   204,052,112   7 HPFS/NTFS
/dev/sda2         302,246,910   312,496,379    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda3         312,496,380   312,576,704        80,325  ef EFI (FAT-12/16/32)
/dev/sda4         204,052,478   302,245,887    98,193,410  15 Unknown


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2028 MB, 2028994560 bytes
55 heads, 54 sectors/track, 1334 cylinders, total 3962880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            251     3,962,879     3,962,629   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7AE0A82DE0A7EE17                       ntfs                                     
/dev/sda2        CCED-990E                              vfat       PE                            
/dev/sda3: PTTYPE="dos" 
/dev/sda4: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        E0A2-163C                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/7AE0A82DE0A7EE17  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetectSince I am new, this is all a learning experience for me. Any help would be awesome as to what the next steps would be.

---

### Post by dino99 on 2010-11-17
[http://ubuntuforums.org/showthread.php?t=1622212](http://ubuntuforums.org/showthread.php?t=1622212)

---

### Post by serkit_ant on 2010-11-18
I had read that thread before I decided to make my own asking about my personal situation. I had also read not to hijack another thread with my own problem, even if the issues were similar. I appreciate the effort, but it didn't help very much. 

I think the EasyPeasy install is on sda4. Now do I put grub2 on sda1 or sda4? Or do I want to use just plain grub?

---

### Post by kansasnoob on 2010-11-18
I've never used Easy Peasy but I see it's Ubuntu derived, anyway something is very wrong with the installation:

> sda3: __________________________________________________ _______________________

File system:
Boot sector type: -
Boot sector info:
Mounting failed:
mount: unknown filesystem type ''

sda4: __________________________________________________ _______________________

File system:
Boot sector type: -
Boot sector info:
Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

Also it shows grub 2 looking at sda5 which doesn't exist:

> => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
partition #5 for /boot/grub.

So please do me a favor and post the output of:

```
sudo parted /dev/sda print
```

It may provide a bit more info about the existing partitions.

Next I'd use the Live USB to create a Windows readable mbr:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

```
sudo apt-get remove lilo
```

Then simply see if Windows will boot under it's own power, hopefully it will.

I may have to study Easy Peasy a bit :)

---

### Post by serkit_ant on 2010-11-18
I put in the command and this was the output:

```
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA ST9160314AS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  104GB  104GB   primary  ntfs         boot
 4      104GB   155GB  50.3GB  primary
 2      155GB   160GB  5248MB  primary  fat32        hidden, lba
 3      160GB   160GB  41.1MB  primary


```

---

### Post by kansasnoob on 2010-11-19
Well, I don't see Ubuntu installed at all, and you have 4 primary partitions which is the limit.

Did you try restoring a Windows readable mbr as instructed?

I really don't know what to do next :confused:

---

### Post by serkit_ant on 2010-11-19
Do I want to put the mbr in sda1 or just in sda or do I put it in the sda4 partitiion. I did the lilo install and during the install it said something about /sbin/lilo. I am so confused....

---

### Post by oldfred on 2010-11-20
Partitions sda3 & sda4 look like they are mislabeled or changed somehow. You do not have an efi partition nor type 15 unknown.

I would try testdisk and see if it says the partitions were something else and if so let testdisk write corrections.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by kansasnoob on 2010-11-20
> **serkit_ant said:**
> Do I want to put the mbr in sda1 or just in sda or do I put it in the sda4 partitiion. I did the lilo install and during the install it said something about /sbin/lilo. I am so confused....

Well there are three commands (as shown in post #4):

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

```
sudo apt-get remove lilo
```

Maybe lilo is not available in EP's repos :confused:

I really don't have hardware that would work with EP so I can't be sure.

Incomplete messages such as "during the install it said something about /sbin/lilo" really tell us nothing. Which command showed that?

Also, you're asking, "Do I want to put the mbr in sda1 or just in sda or do I put it in the sda4 partitiion" and you can see from this command:

```
sudo lilo -M **[COLOR="Red"]/dev/sda[/COLOR]** mbr
```

It's sda!

Did you copy-n-paste the commands?

---

### Post by serkit_ant on 2010-11-28
Well I used testdisk to delete all the partitions except the windows recovery partition. I installed easypeasy without making new partitions. I can boot the recovery partition if needed and install windows, but I don't need to right now. I got all my important stuff (music, photos, etc.) backed up so I didn't lose everything that I wanted to save anyways, except for maybe iTunes for my itouch. I am just going to figure out a way to do it all in linux. It shouldn't be to difficult. I am starting to get the hang of using the terminal more.:)

---

