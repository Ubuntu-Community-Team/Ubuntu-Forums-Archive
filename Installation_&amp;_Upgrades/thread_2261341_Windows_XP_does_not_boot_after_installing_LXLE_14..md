---
title: "Windows XP does not boot after installing LXLE 14.04 in Dual-Boot"
date: 2015-01-18
forum: Installation &amp; Upgrades
---

### Post by 410172 on 2015-01-18
(LXLE 14.04 -> LUbuntu LTS 14.04)

Hello,

A few days ago I found out that Windows 7 was a bit too much for one of my old computers. When searching for a replacement for Windows 7 OS I came across LXLE. I decided to try it out. As it is a Linux OS, I decided to make it dual-boot with an older Windows version, Windows XP, so that I still could play my old Windows games on the PC.

First, I installed Windows XP Home Edition. After I got that to work, I burned LXLE 14.04 (64-bit) onto a disk and installed that. It recognized the Windows OS and as selected it set up a dual-boot for me. I could set sizes for partitions in the installer and everything seemed fine. After installation, I restarted the computer and checked if all OSes were working. LXLE worked fine, yet I was not able to boot into Windows XP. It just showed a black screen with a flashing white stripe at the upper left. Normally you would see that for a few seconds before your OS would boot, nothing else happened though.

Booting back into LXLE, I used GParted to check whether the Windows partition had a boot flag, it had one so I installed Boot-Repair to see if it could find and fix any problems. It showed success, yet there was no change and Windows XP was still unaccessable. Link: paste.ubuntu.com/9766403. 
I don't know why it is not working; I do know it is not a problem in the installation of Windows, as I started Windows normally without problems and made sure it was ok before I moved on to installing LXLE. 

I did get this error when running the command "parted -l":
Error: /dev/zram0: unrecognised disk label

==============ls gives ls: cannot access : No such file or directory

=================== hexdump -n512 -C /dev/sda1: here are some Dutch lines in the text, they mean: Error in reading disk. NTLDR is missing. NTLDR is compressed. Press CTRL-ALT-DEL to restart.

I did not see anything else strange in the boot repair summary, I could be wrong though as I have no knowledge of it at all. Those things above just, well, took my attention.

I hope someone can tell me what went wrong and how I can get my Windows XP to boot again. If possible, without reinstalling the whole thing. Not because I need to save any data (did nothing with both OSes after installing yet), just because it takes a lot of time to do it all again.

Thanks in advance.

---

### Post by nerdtron on 2015-01-18
HHmmm.. windows partition is still intact. and ubuntu looks like installed correctly.

Can you boot into ubuntu and run update grub from the terminal:
```
sudo update-grub
```
You'll be asked for your password and asterisks will not be shown. press enter when you typed your password
Post the output of that command here.


Also, regarding your command parted -l, can you try it with sudo:
```
 sudo parted -l
```

---

### Post by efflandt on 2015-01-18
When installing Linux along with Windows XP it is probably best to install WinXP on a limited size partition leaving unallocated space on the drive to install Linux.

Otherwise if WinXP is already installed, first make a note of its virtual memory size and disable that in Windows (similar to swap, which in Windows cannot be moved), then defrag the drive to make sure that all files are down low on the drive. Then from live/install Linux iso (on DVD or USB) shrink the Windows partition with gparted in Linux (which will mark the partition dirty), reboot Windows and let it do its drive check to make sure everything is fine. At that point you could re-enable virtual memory in Windows. Then install Linux.

If you do not disable virtual memory and defrag XP before shrinking its partition, the amount you can shrink its partition may be limited. I learned that many years ago when I could only shrink a 200 GB WinXP drive by 24 GB. Much later I discovered that I could free up 150 GB or more on that same drive by disabling WinXP virtual memory.

The procedure is different for Win7 (and maybe Vista) where you would use Windows' own Disk Management to shrink its partition.

---

### Post by 410172 on 2015-01-18
sudo update-grub gives me the following:

Generating grub configuration file...
Found background image: splash.png
Found Linux image: /boot/vm-linuz-3.13.0-38-generic
Found initrd image: /boot/initrd/img-3.13.0-38-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
Done

sudo parted -l gives:

Model: ATA Hitachi HDS72161 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition table: msdos

Number  Start        End        Size          Type          File system          Flags
1            32.3KB    100GB    100GB       primary      NTFS                  boot
2            100GB     160GB    60.0GB      extended    
5            100GB     157GB    57.3GB      logical        ext4
6            157GB     160GB    2673MB     logical        Linux-swap(v1)

Error: /dev/zram0: unrecognised disk label

I heard about the virtual memory issue. I did not do anything in Windows XP after installing except for changing screen resolution. I shut the computer down and started installing LXLE. I just got to swipe sizes for Windows and LXLE in the LXLE installer. The drive is 160 GB, so I got the following:
Windows XP Home Edition: 100 GB - LXLE 60.0 GB.
It installed and created a bootloader. Everything seemed fine until I tried to boot into Windows.

Thanks for the fast replies. I really apprieciate that.

---

### Post by oldfred on 2015-01-18
I might temporarily reinstall the Windows boot loader to the MBR and see if Windows boots. If not make repairs. Grub really only boots a working Windows system.
You can use Boot-Repair to install a Windows boot loader and later restore grub using advanced mode. 
Or you just use your XP install disk to run fixMBR to restore a Windows boot loader. 
Then run fixBoot and chkdsk.

 XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

   Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

   FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

Do not use XP to go onto Internet. If games are older and run in XP, then may run in .wine, but you would have to test that.

---

### Post by Mishy.hu on 2015-03-12
Hi!

I had a very similar issue and I could manage to fix it last night!

This is my type of solution, I hope it will help some people in the future:

I had a system (Dell Latitude D620), which had a Windows XP Pro which came with the laptop when I bought in 2007.
It has changed it's home several times in the last years, even to larger HDD or same with no issues.
Last move included an OS (Linux distro) change also.
New system is a Xubuntu 14.04.
The new HDD was formatted with a new set of system tools, specially the fdisk is different.
On new system the starting block for the first partition is **2048** insted of the old **63**!

Basically I had also a lonly blinking cursor when I tried to boot the XP.

If I booted with Windows XP CD-ROM, then used Repair, 1, ENTER, Admin-PWD:
FIXMBR
FIXBOOT
BOOTCFG /REBUILD
this last one gave me error about damaged FS
CHKDSK C: /R fixed it, but later on there was no reported "fixed" message on next CHKDSK, but "BOOTCFG" still errored.

After REBOOT:
"Error loading operating system"
message was the only sign of the Windows.

The system:

***Old HDD:***
Seagate Momentus 7200.4
ST9500420AS
500 GB

partitions:
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          **63**    15020774     7510356    7  HPFS/NTFS/exFAT
/dev/sdc2        15020775    63263969    24121597+  83  Linux
/dev/sdc3        63263970    63456749       96390   83  Linux
/dev/sdc4        63456750   976768064   456655657+   f  W95 Ext'd (LBA)
/dev/sdc5        63456813   123475589    30009388+   c  W95 FAT32 (LBA)
/dev/sdc6       123475653   142239509     9381928+  83  Linux
/dev/sdc7       142239573   153195839     5478133+  83  Linux
/dev/sdc8       153195903   177437924    12121011   83  Linux
/dev/sdc9       177437988   976768064   399665038+  83  Linux


[B]*New HDD:*
Samsung SSD 840 EVO 1TB[/B]

partitions:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        **2048**    15022760     7510356+   7  HPFS/NTFS/exFAT
/dev/sda2        15022761    16071336      524288   83  Linux
/dev/sda3        16071337   162871976    73400320   83  Linux
/dev/sda4       162871977  1942871977   890000000+   f  W95 Ext'd (LBA)
/dev/sda5       162874025   246760104    41943040    c  W95 FAT32 (LBA)
/dev/sda6       246762153   257247912     5242880   83  Linux
/dev/sda7       257249961   269832872     6291456   83  Linux
/dev/sda8       269834921   278223528     4194304   82  Linux swap / Solaris
/dev/sda9       278225577  1942871977   832323200+  83  Linux

_**Procedure:**_
[COLOR=#ff0000]CAUTION! You can definitely DAMAGE your system if you mistype something here!
USE IT FOR YOUR RESPONSIBILITY![/COLOR]

This step can be done under your Linux system, but I did it under a Live Xubuntu 14.04 using the installer USB-stick.
I copied to the /home partition (which lays on /dev/sda9 in my case; => *of=/tmp/MOUNTED-SYSTEM/home/sda1*)
but if one has way larger Win-partition, or small room on Linux, may use an external HDD to do so.

Save the Windows partition (in my case WINPARTITION=/dev/sda1)
Open a terminal (ie: CTRL+ALT+T)
[SIZE=3][FONT=fixedsys][B]sudo su -
dd if=/dev/$WINPARTITION of=/some/path/to/$BACKUP[/B][/FONT][/SIZE]

*delete and recreate the Windows-partition:*
root@xubuntu:~#[SIZE=3] [FONT=fixedsys]**fdisk -c=dos /dev/sda**[/FONT][/SIZE]
**d** [COLOR=#808080]# delete[/COLOR]
**1** [COLOR=#808080]# partition 1
[/COLOR]**n** [COLOR=#808080]# new[/COLOR]
**p** [COLOR=#808080]# primary[/COLOR]
**1** [COLOR=#808080]# partition 1
[/COLOR]First sector (63-1953525167, default 63):**<ENTER>** Using default value 63
Last sector, +sectors or +size{K,M,G} (63-15022760, default 15022760): **15020774 **[COLOR=#808080]# This one is the calculated end, from your actual saved partition size[/COLOR]
**t **[COLOR=#808080]# FS-type[/COLOR]
**1** [COLOR=#808080]# partition 1[/COLOR]
**7** [COLOR=#808080]# HPFS/NTFS/exFAT[/COLOR]
**a** [COLOR=#808080]# make it active[/COLOR]
**1** [COLOR=#808080]# partition 1
[/COLOR]**w** [COLOR=#808080]# write it to the disk[/COLOR]

At this point I got:
[I]WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
[/I][FONT=fixedsys]**hdparm -z /dev/sda**[/FONT] also failed.Reboot the LIVE-Linux, the partitions now OK. There is a small gap between the first two partition, but it is a small price for the benefit:
...
/dev/sda1   *          63    **15020774**     7510356    7  HPFS/NTFS/exFAT
/dev/sda2        **15022761**    16071336      524288   83  Linux
...

Copy the Windows back:
[SIZE=3][FONT=fixedsys]**su -**[/FONT][/SIZE]
mount your backup partiotion/disk again if needed (where the partition backed-up before)
in my case
[SIZE=3][FONT=fixedsys][B]mkdir /tmp/MOUNTED-SYSTEM
mount /dev/sda3 /tmp/MOUNTED-SYSTEM[COLOR=#a9a9a9] # this point is not important [/COLOR]
mount /dev/sda9 /tmp/MOUNTED-SYSTEM/home[/B] 
***dd if=/tmp/MOUNTED-SYSTEM/home/sda1 of=/dev/*[B]$WINPARTITION** [/B][COLOR=#808080]# of=/dev/sda1 in this case[/COLOR]
[/FONT][/SIZE]
If you reboot now from HDD it should start right into Windows!

Now you can reinstall GRUB2
Reboot into Live-Linux:
Open terminal
[B][SIZE=3][FONT=fixedsys]su -
mkdir /tmp/system[/FONT][/SIZE][/B]
Mount the complete Linux partition hierarchy
In my case
[B][SIZE=3][FONT=fixedsys]mount /dev/sda3 /tmp/system
mount /dev/sda2 /tmp/system/boot
....[/FONT][/SIZE][/B]
then:
[SIZE=3][FONT=fixedsys][B]mount --bind /sys /tmp/system/sys
mount --bind /proc /tmp/system/proc
mount --bind /dev /tmp/system/dev
chroot /tmp/system
grub-install /dev/sda
exit
reboot[/B][/FONT][/SIZE]

You are all set!

---

### Post by oldfred on 2015-03-12
@mishy.hu

You do not want to use the old sector start of 63 with any new 4K hard drive nor SSD. The purpose is to make sure you do not have to write to two sectors every  time. 
And XP does not support ACHI, so you will not be running trim, so once SSD gets full it will slow down even more.

       [https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)
Alignment 2048 sectors Advanced Format drives
[http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted](http://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted)

---

