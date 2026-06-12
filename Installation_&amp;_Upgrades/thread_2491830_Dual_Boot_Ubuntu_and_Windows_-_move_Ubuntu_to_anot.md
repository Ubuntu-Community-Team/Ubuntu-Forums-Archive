---
title: "Dual Boot: Ubuntu and Windows - move Ubuntu to another drive"
date: 2023-10-22
forum: Installation &amp; Upgrades
---

### Post by francwalter on 2023-10-22
Hallo

Some months ago I have installed Ubuntu 22.04 on an empty 400 GB HDD in my PC where I mainly work with Windows 11 (on a 500 GB SSD). But Ubuntu is quite useful, so from time to time I work there.

I have now dual boot with Ubuntu or Windows, which works very well. Only that the HDD with Ubuntu, when I boot it, makes a lot of typical HDD-noises, its an old HDD and I fear that it could smoke down.

Recently I added a SSD with 2 TB to the Computer and now I would like to move Ubuntu to that drive, using the old 400 GB HDD as backup only.
But I would like to split the SSD into 2 partitions: 2 x 1 TB, leaving 1 TB for Windows (I use it there for VMware VMs).

I would like it like this: in the Boot manager I have 2 x Ubuntu (on the old 400 GB HDD and on the new 1TB partition on SSD) and Windows as before.
I would use Ubuntu on the 1TB partition and Windows as before. The old Ubuntu on the 400 GB HDD I would not use (normally).
From time to time I would clone the Ubuntu partition from that 1TB SSD partition to the 400 GB HDD to have a backup, in case if the 2TB SSD would smoke away.

Is this easy to do?
How?

Thanks for hints.
frank

**EDIT (after problem solved) 2023-10-25:** *Short summary:* I cloned the drive using a live system (22.04.3 Desktop Ubuntu on a USB-Pen-Drive) with Gparted but then I had to change the UUID of the dest. drive (/sdd2, which was then identical to the source drive /sdc1, because cloned) and run again update-grub. So directly after cloning I should have changed the UUID of my dest. drive (/sdd2) and run update-grub then it would have been fast, maybe an hour. See the end of this thread.

---

### Post by MAFoElffen on 2023-10-22
I'll summarize the thoughts I have on this, then add details to it once we find out the details on your system, to accomplish that... There are many, many, many ways to do that, this is just one way...

The easiest way I can think of is to create a clonezilla backup, then restore it to the new drive... After the restore, resize the partitions to what you want on the new drive.
RE: [https://www.tecmint.com/linux-centos-ubuntu-disk-cloning-backup-using-clonezilla/](https://www.tecmint.com/linux-centos-ubuntu-disk-cloning-backup-using-clonezilla/)

---

### Post by francwalter on 2023-10-22
Thanks!
My 2TB SSD is already partly in use by Windows. 
I would do it like that:
I resize the 2TB SSD volume (sdd) in Windows from 2TB to 1TB, keeping my Windows files (VMs) on the first 1TB partition. Now I would boot my PC with a clonezilla live boot stick (I have it already) and clone my actual Ubuntu partition (sdc) to the new partition (I guess sdd2).

But now, how do I add this Ubuntu partition on sdd2 to Grub Bootloader?
This is still unclear to me.

---

### Post by MAFoElffen on 2023-10-22
I guess I misunderstood what you described... I thought you were adding a blank drive to your PC to replace the current external drive you have now, where you would just have to boot from the new drive.

Doing it this new ay, that I now understand, you would jst add a partition (or few) to the internal drive, and copy over the partitions.. Being careful not to over write the existing EFI partition, then fix the fstab file to the new filesystem mounts it's going to have... then reinstall grub, so that it adds the new entries to the existing EFI partiton on that drive.

It would be easier, since you are already shrinking the Windows partition (using Windows tools to do that) to make room for it to live... To just install fresh/new without the external drive connected. Then once installed and running, connect the external drive to migrate your data to the newly install instance. Less work, and you have an unchanged backup of your data on that old drive. Right?

When you are 100% sure you have everything copied over to the new installation and it is working... Then frag that old drive, and use it as external storage for your backups.

---

### Post by oldfred on 2023-10-22
I prefer new clean install, which housecleans all cruft. Use Something Else to choose correct partition(s) for your install.

And then restore from your normal backup. Becomes good test that backup has everything you need including /home, list of installed apps, other data or system settings in / that you changed from defaults, but not all of system in / (root). 

Do not use image as backup. Better to just use rsync to copy changes to old drive.

---

### Post by MAFoElffen on 2023-10-22
+1 with oldfred. --

Testing the Restoring of your backups onto the new media gives a good test of how good they do work and will build confidence in your backup strategy.

rsync will carry over the permissions that were there. Just a basic copy of files will not. <-- Especially if you copied them to your Windows machine to ntfs. That will lose all the Linux permissions.

---

### Post by francwalter on 2023-10-23
I still don't understand.
I don't want to reinstall again, I have no "cruft" which I would need to clean, my system is just installed, some months ago, I am happy now with it.
New install would mean a lot of work!
I try to make it clearer how my system is configured:

1st Drive in my PC is a 500 GB SSD, Windows on it. I can select Windows in the boot loader (and also Ubuntu). Ubuntu calls this drive sda. The windows partition is sda3. 

2nd Drive is a 2TB HDD, for Windows data. I did not mentioned that drive before, as it is not relevant. It's sdb in Ubuntu counting. 

3rd Drive is a 400 GB HDD, Ubuntu on it, I can select it in the bootloader (and also Windows, see above). Ubuntu calls this drive sdc. 

4th Drive is a new 2 TB SSD ("sdd"), at the moment NTFS for Windows. I could delete (move) all data if necessary to make partition and format easier, but I think it could be possible to just shrink the size and make 1TB place for the new Ubuntu partition.

So what I thought is, that I clone my Ubuntu partition from the 2nd drive to the 2nd partition of the 4th drive and tell the boot loader (grub) that please show this partition in the boot selection too. As Ubuntu main e. g. 

Maybe I am wrong when I think that the bootloader is on the 1. drive?
If the bootloader is on the 3. drive (with actual Ubuntu) then I would need to move the bootloader to the 2. partition of the 4. drive?
I am still not clear about EFI partitions and where the bootloader is. 

If it would be easier to delete the 4th drive completely and use it fully for my copied Ubuntu I could do it, then I would save my windows stuff (VMs) just on another external drive.

I hope it's clearer now :)
Thanks!

---

### Post by tea for one on 2023-10-23
Together with oldfred and MAFoElffen, a clean installation and restore backups would be ideal.
If you wish to further explore your idea, then more info is needed.
> **francwalter said:**
> 
Maybe I am wrong when I think that the bootloader is on the 1. drive?
If the bootloader is on the 3. drive (with actual Ubuntu) then I would need to move the bootloader to the 2. partition of the 4. drive?
I am still not clear about EFI partitions and where the bootloader is.
As you are not sure of the details, then you should be very careful before proceeding.
Your final objective may be possible with a little modification and a cautious approach.
Please boot into Ubuntu, open a terminal and enter:-
```
sudo parted -l
```
Please post command and output (using code tags)
> If it would be easier to delete the 4th drive completely and use it fully for my copied Ubuntu I could do it, then I would save my windows stuff (VMs) just on another external drive.
It would be easier to clone Ubuntu starting at the beginning of the drive and then using the spare space for ntfs storage at the end.

It is essential to see the partition details to verify if your objective is feasible.

---

### Post by francwalter on 2023-10-23
> **tea for one said:**
> ...
```
sudo parted -l
```
...
This comes out:

```
#sudo parted -l
Modell: ATA Samsung SSD 840 (scsi)
Festplatte  /dev/sda:  500GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: gpt
Disk-Flags: 

Nummer  Anfang  Ende   Größe  Dateisystem  Name  Flags
 1      1049kB  368MB  367MB  ntfs               msftdata
 2      368MB   499GB  499GB  ntfs               msftdata
 3      499GB   500GB  105MB  fat32              boot, esp
 4      500GB   500GB  576MB  ntfs               versteckt, diag


Modell: ATA WDC WD20EARX-00P (scsi)
Festplatte  /dev/sdb:  2000GB
Sektorgröße (logisch/physisch): 512B/4096B
Partitionstabelle: msdos
Disk-Flags: 

Nummer  Anfang  Ende    Größe   Typ      Dateisystem  Flags
 1      32,3kB  2000GB  2000GB  primary  ntfs


Modell: ATA ST3400833AS (scsi)
Festplatte  /dev/sdc:  400GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: gpt
Disk-Flags: 

Nummer  Anfang  Ende   Größe  Dateisystem  Name  Flags
 1      1049kB  400GB  400GB  ext4


Modell: ATA Fanxiang S101 2T (scsi)
Festplatte  /dev/sdd:  2048GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: gpt
Disk-Flags: 

Nummer  Anfang  Ende    Größe   Dateisystem  Name                          Flags
 1      17,4kB  16,8MB  16,8MB               Microsoft reserved partition  msftres
 2      16,8MB  2048GB  2048GB  ntfs         Basic data partition          msftdata


```
And this shows gparted for sda, sdb, sdc and sdd, see attached screenshots.

---

### Post by tea for one on 2023-10-23
Disk sda is Windows with an ESP
Disk sdc is your Ubuntu installation but it doesn't have an ESP

Each OS on a separate disk is ideal.
However, in order to be more robust in the future, each disk should have an ESP
Then, you have a way to boot either OS via your PC boot menu

I would _not_ recommend that you clone your Ubuntu OS without an ESP.

I would suggest the following:-
Back up all your data
Isolate or physically remove sda, sdb and sdc
Only have your target disk accessible - sdd at the moment
Boot into the Ubuntu installer in UEFI mode
Create a GPT (partition table)
The installer will create an ESP automatically
Finish the installation
Restore your Ubuntu data

Then, you can decide how much space you need for Ubuntu and subsequently create an ntfs partition on your new 2TB disk

---

### Post by oldfred on 2023-10-23
Please do not post in line. Not everyone has high speed Internet.
 If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots or other info. Post #4 , also no larger than1024x768 if photo
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

A good backup and restore would not require any extra effort, you need to have good backups, if you think you have a configuration you want to keep & its a lot of work to recreate it.
We often see users who try to clone a system and have to spend days correcting it.

All user configurations are in /home. 
Only if you changed some system settings like grub or fstab may you want to also copy those.
You are in best case as having old install, so if restore of backup is not complete, you still have old drive to go back and get any missing data. Often list of installed apps & restore is the longest process.

What to backup TheFu, some of these are the  same info:
[https://ubuntuforums.org/showthread.php?t=2456011](https://ubuntuforums.org/showthread.php?t=2456011)
[https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507](https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507)
[https://ubuntuforums.org/showthread.php?t=2484708](https://ubuntuforums.org/showthread.php?t=2484708)
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) &
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992) & 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

---

### Post by MAFoElffen on 2023-10-23
Another idea to throw out there... This morning I am going to spin up a VM to test the details and idiosyncrasies of this for the just in-cases. To make sure it really works, and ensure I give you the right details. I know this is possible, but want to make sure it really works for you before I fully get behind it as a solution. Understood?

#1 -- Backup your Ubuntu Install! That is a given before making any major changes to a system. Always have a fall-back to get back to where you started.
#2 -- You said you are going to shrink down your 2TB disk's NTFS partion to 1TB, so that you had 1TB un-allocated on it for Ubuntu. Do that from within Windows Disk Manager.
#3 -- Boot from an Ubuntu Installer LiveUSB > "Try" > Start GParted.
#4 -- From within GParted, select the disk that has your old Ubuntu partition. When that disk is displayed, click on that ext4 partition, then right click on it. Select "Copy".
#5 -- From within GParted, select the 2TB disk that is your target disk where you want to copy Ubuntu to... Select the un-allocated space. Right click on it, and select "Paste".
#6 -- From there GParted will pop up a window, letting you resize the partition into the unused space... You can resize the new partition at that time. > Then select the "Paste" button from that window.
#7 -- From within GParted, select "Apply". That partition will then be cloned on that new disk.
#8 -- After it is cloned, exit GParted and shutdown the system.

That will get that onto that disk. But it can't boot that yet. That should keep you busy for a long while. In the mean time, I'll work out the details on the easiest way to get it to boot, and to remove the old disk with the original Ubuntu installation.

I'm thinking of two different ways. Either via booting the old Ubuntu and running update-grub... and seeing if OS_Prober picks it up. The problem with that is that the UUID's of the filesystem are going to be the same. Or by just removing the old disk, booting from something bootable, chrooting into the new, and reinstalling Grub.

If that is really what you want to do, then I'll figure out what might be easiest for you to pursue.

Ideas? Thoughts? Or am I wasting my time, and that is not what you really want? I'm open to helping you with that, if this is the path you want to take.

---

### Post by francwalter on 2023-10-23
Oh, Thank you!
OK, my thoughts are, that I could clean the sdd (2TB SSD) from Windows partitions and install Ubuntu on it with USB Live Stick, to get ESP on it (as T41 adviced). I already copied the data from the Windows partition to a backup, so I can delete and partition sdd.
But couldnt I get ESP on it with Gparted too?
Boot with a Live Stick and create the partition with Gparted, then copy and paste how you proposed?

Or what would happen, if I installed Ubuntu on sdd, would Ubuntu notice, that there is Windows and another Ubuntu already installed? Would propose to add the new Ubuntu on sdd to the boot loader on sda?

My problem with fresh install and restore a backup (from "old" Ubuntu) is, that I have many system changes too. After installing a OS usually I do a lot of changes on many spots, surely system files too. All system stuff I dont like, I change it :(
I could copy /home and /opt but this wont restore my whole system. And I doubt that I could restore /sbin and /bin without strange results. All installed programs they have data on different spots, I dont know where they all are.

I have a Raspberry Pi 3B with a MicroSD card for the system. Here I do daily a copy of the whole sdcard to another MicroSD card. If the main sdcard smokes down, I (hopefully) just switch the sdcard and on it goes. I thought it could go on Ubuntu easy as that.

---

### Post by oldfred on 2023-10-23
Unless you are installing web, database or virtual installs, you probably are not changing anything in /'s settings. All user settings are in /home in . hidden files & folders. 
Linux is a multiple user system where each user can have unique settings.

I do edit grub, fstab & network settings, but have scripts to do the same edits. I also copy each of those files to /home folder so my backup of /home includes those files. And /home without data or just the configuration files is tiny. I have all data in separate data partition so I can use it with several installs. My /home per du is 1.5GB. I also do not install any snaps which may  be in /?

Did I just say 1.5GB is tiny? 
I once thought a 5MB hard drive was huge. And having 4 16KB memory boards gave me a huge amount of RAM.

---

### Post by MAFoElffen on 2023-10-23
Warning = off topic...

Oh Dang... 1980's. My first 10MB HDD. Thought I would never fill up that much room with DOS. Then the larger disks came out that required special disk management software just to boot. The balancing act of loading things in high-mem above 640K... Fun times.

Now I don't even winch at allocating GB+ swap files on the fly because I have the free storage there. And memory balancing is an unneeded lost art.

Linux is so much easier.

I'm feeling old. LOL

Back On Subject --
Yes, that latest version of your plan in Post #13 with +1 with oldfred's last post (#14) sound like a much easier and better plan.

---

### Post by francwalter on 2023-10-23
I am confused. Which plan of mine in #13 do you mean?

To be clear: I dont want to copy the system, I want to clone it. Backup and Copy means installing programs and spend hours and hours (and more hours) to get all back.

---

### Post by MAFoElffen on 2023-10-23
Nevermind... I spun up Machine to document what the cloned partition move with GParted would look like. It's actually pretty easy and painless to do.

Here is the example starting out as it looks from a LiveUSB right after I installed Windows for your example:
```

mafoelffen@win10-mantic-test:~$ lsblk -e7 -o name,label,size,fstype,mountpoint
NAME   LABEL                      SIZE FSTYPE  MOUNTPOINT
sda                               160G         
&#9500;&#9472;sda1                            100M vfat    /boot/efi
&#9500;&#9472;sda2                             16M         
&#9500;&#9472;sda3                          159.4G ntfs    
&#9492;&#9472;sda4                            509M ntfs    
sdb                                60G         
&#9492;&#9472;sdb1                             60G ext4    /
sr0    Ubuntu 22.04.3 LTS amd64   4.7G iso9660 /media/mafoelffen/Ubuntu 22.04.3 

```
Similar to yours, in that it only has one UEFI partition for both Windows and Ubuntu. With Ubuntu on the second disk. (that shown below, but after I shrank the Windows partition...)

This is what it looks like after shrinking the partition from the Windows Disk Manager...
```

ubuntu@ubuntu:~$ lsblk -e7 
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
sda      8:0    0  160G  0 disk 
&#9500;&#9472;sda1   8:1    0  100M  0 part 
&#9500;&#9472;sda2   8:2    0   16M  0 part 
&#9500;&#9472;sda3   8:3    0 81.3G  0 part 
&#9492;&#9472;sda4   8:4    0  509M  0 part 
sdb      8:16   0   60G  0 disk 
&#9492;&#9472;sdb1   8:17   0   60G  0 part 
sr0     11:0    1  4.7G  0 rom  /cdrom

```
Then what it look slike after cloning the partition over with GParted.
```

mafoelffen@win10-mantic-test:~$ lsblk -e7 -o name,label,size,fstype,mountpoint
NAME   LABEL                     SIZE FSTYPE  MOUNTPOINT
sda                              160G         
&#9500;&#9472;sda1                           100M vfat    /boot/efi
&#9500;&#9472;sda2                            16M         
&#9500;&#9472;sda3                          81.3G ntfs    
&#9500;&#9472;sda4                           509M ntfs    
&#9492;&#9472;sda5                          78.1G ext4    
sdb                               60G         
&#9492;&#9472;sdb1                            60G ext4    /
sr0    Ubuntu 22.04.3 LTS amd64  4.7G iso9660 /media/mafoelffen/Ubuntu 22.04.3 L

```
As you can see OS_PROBER found the moved installation at /dev/sda5...
```

mafoelffen@win10-mantic-test:~$ sudo update-grub
[sudo] password for mafoelffen: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-35-generic
Found initrd image: /boot/initrd.img-6.2.0-35-generic
Found linux image: /boot/vmlinuz-6.2.0-26-generic
Found initrd image: /boot/initrd.img-6.2.0-26-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Found Ubuntu 22.04.3 LTS (22.04) on /dev/sda5
Adding boot menu entry for UEFI Firmware Settings ...
done

```
I shtu down th machine, removed the second disk,. Booted it up, and selected the new Ubuntu from the Grub menu... This is what it looks like from that instance, without the second sik attached.
```

NAME   LABEL                     SIZE FSTYPE  MOUNTPOINT
sda                              160G         
&#9500;&#9472;sda1                           100M vfat    /boot/efi
&#9500;&#9472;sda2                            16M         
&#9500;&#9472;sda3                          81.3G ntfs    
&#9500;&#9472;sda4                           509M ntfs    
&#9492;&#9472;sda5                          78.1G ext4    /
sr0    Ubuntu 22.04.3 LTS amd64  4.7G iso9660 /media/mafoelffen/Ubuntu 22.04.3 L
mafoelffen@win10-mantic-test:~$ sudo update-grub
[sudo] password for mafoelffen: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-35-generic
Found initrd image: /boot/initrd.img-6.2.0-35-generic
Found linux image: /boot/vmlinuz-6.2.0-26-generic
Found initrd image: /boot/initrd.img-6.2.0-26-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done

```
I then re-ran update-grub to re-generate the gurb.cgf with the old install (that wasn't there any more...

Done. It didn't take that much time. BUT... Cloning is still copying data from one place to another. So what you said about not making or restoring data, doesn't make any sense, because.... That is also copying and moving data. You see that right? 

Yours was a fresh install. True you don't have any cruft. and this would be less time installing new apps and making the config changes you have made.

I hope this helps.

---

### Post by francwalter on 2023-10-24
First thing: THANK A LOT FOR YOUR TIME to test this scenario on your vms :) very appreciated :) :)
By the way: my setting is with more drives than yours (4 instead of 2, but one, sdb, not relevant at all) and the new Ubuntu will not be on the same drive than windows, but this are not relevant differences, I guess.

OK then, I created a new USB-Flashdrive with Ubuntu 22.04.3 LTS (I had one with Ubuntu 22.04.1 LTS which gave me that wellknown "Verfication failed: (0x14) Security Violation" ERROR) and started the computer with it.
It was a bit weird, no GUI and no choice to try only - I installed the Server instead the Desktop version on my Flash Drive :) :) :)

Anyway, I installed Ubuntu 22.04 Server on the SSD drive (sdd, 2 TB) which I had previously cleaned and backed up, see screenshot. The installer created an EFS and ext4 Partition on the 2TB sdd.
So this was quick done and the Grub was updated, now I have 2 Ubuntu boot entries :)

Next I will do is create a real Try-Ubuntu Stick (at the moment downloading, ubuntu-22.04.3-desktop-amd64.iso) and then I will copy ("clone") with Gparted the old Ubuntu on the new Ubuntu, will edit this post then later ...

**EDIT 24.10.2023 at 18:32: **at the moment with live Ubuntu I am cloning with Gparted. It says in Details (copy /dev/sdc1 to /dev/sdd2)
```
e2image -ra -p '/dev/sdc1/' '/dev/sdd2'
```
37.000.000 / 50.765.301 blocks (72%) 00:16:00 at 56 MB/S

I am curious if I can easily shrink sdd (the 2TB SSD) later, as the old Ubuntu was on a 400 MB drive and I didnt change the 2TB size yet. I think it would have been better to do it before the copy, because if it wont work, e.g. if there is data loss, I have to copy again.

---

### Post by francwalter on 2023-10-24
OK, I am back on Windows. Not all went well, I guess I deleted Grub on sdd by copying old Ubunto over it, because now, I have a black screen with a plain text "grub" command line and no boot loader anymore.
It says there: 
> GNU Grub version 2.06 
Minimal BASH-like line editing is supported. For the first word... ... ...
grub> 
I can switch with my BIOS (with F11) to another disk as boot volume, so I came back to my old Ubuntu boot loader and could select Windows there (or old Ubuntu), so no real worries.

But how can I reinstall grub on the sdd now? 
Can I reinstall from that grub command line?
I attach an image to show how this looks. On the picture with the BIOS Boot menu, the third one is my old Ubuntu Grub, the first is the new one, now broken, the default boot loader (yes, I can change the default).

EDIT: Oh, sorry, I forgot to do a simple search (for: "Minimal BASH-like line editing is supported") and found immediately results, e.g. this: [Fix Minimal BASH like line editing is supported GRUB Error In Linux]("https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/")

---

### Post by oldfred on 2023-10-24
Is your sdd, MBR(msdos) or gpt(GUID)? See disklabel type & post in code tags:
sudo fdisk -lu

Windows requires gpt for UEFI boot, Ubuntu lets you use MBR with UEFI, but really should not. You always want gpt.

And your sdd3 is huge for a FAT32 partition. FAT32 does not support files over 4GB nor has journal to make repairs easier or faster. If intended for data for Windows use NTFS, if data for Linux use ext4 or other Linux format.

---

### Post by MAFoElffen on 2023-10-24
+1 -- Yes, and when you buy a new drive, if external, a lot of those, for some reason, are pre-partitioned with the old MS-DOS partitions... That is why my usuall go-to first step is to just add a fresh GPT partition table to new drives when they first get here.

I made that mistake "once" and it caused me a whole lot of work a year later when I finally noticed there was a problem caused by that. Now, I just assume that they are not GPT and overcompensate for that. I try to learn from my mistakes. LOL

---

### Post by francwalter on 2023-10-24
I have still no boot entry for the new (copied) Ubuntu on sdd2, at least I could fix the old one, with Live USB-Drive and "boot-repair", but the other ways didnt work (prefix etc.)
So now I have grub with two Ubuntu, but both are the old one on sdc, not on sdd, as it shows in the Grub Customizer (see attached screenshot).

I wonder if I could manually edit the grub config to really add sdd2 to the boot. I tried it with update-grub (as you did on the vm test):

```
#update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-35-generic
Found initrd image: /boot/initrd.img-6.2.0-35-generic
Found linux image: /boot/vmlinuz-6.2.0-34-generic
Found initrd image: /boot/initrd.img-6.2.0-34-generic
Found linux image: /boot/vmlinuz-5.19.0-46-generic
Found initrd image: /boot/initrd.img-5.19.0-46-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda3@/EFI/Microsoft/Boot/bootmgfw.efi
Found Ubuntu 22.04.3 LTS (22.04) on /dev/sdd2
Adding boot menu entry for UEFI Firmware Settings ...
done
```

I have grub now on both, on sda (where I can read sdd in the selection) and sdd, but on both it is the old Ubuntu which starts.
When I select in the BIOS boot device sda, I see sdd in the grub menu but it will start sdc (old Ubuntu).
So till now I even can't say if my cloning worked.
By the way, I reformatted from fat32 to ntfs.
Not a problem

---

### Post by MAFoElffen on 2023-10-24
> **francwalter said:**
> 
...
as it shows in the [COLOR=#ff0000]Grub Customizer[/COLOR] (see attached screenshot).
...
By the way, I reformatted from [COLOR=#ff0000]fat32[/COLOR] to [COLOR=#ff0000]ntfs[/COLOR].
...

::Chewing Through Lip:: ](*,)

Others can take this from here... I've done my part.

---

### Post by oldfred on 2023-10-24
Also not a fan of Grub Customizer. 
It totally replaces grub's scripts with its own proxy files. Then no idea what they do.

Post link to summary report from Boot-Repair. How you say you are booting sounds like duplicate UUIDs so system only boots one of the two. Duplicates not allowed.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)
    Note that grub only boots working 

Please review my first post where I said install works and some image type copies can take days to resolve.
My laptop needed Windows recovery. So it totally erased my Linux partitions (many).
I will keep track of time to install. But I install from grub2 loopmounted ISO on one drive with toram, to NVMe drive. So install is from RAM to NVMe or very fast. Since laptop, I do not really have backup, but all data is on desktop & just rsync'd over. Laptop is a copy of data and will copy is better than nothing, not really a backup.

---

### Post by francwalter on 2023-10-25
[Pastebin of boot-repair]("https://pastebin.ubuntu.com/p/BvJVJV5rqs/")
I had followed a way to repair "[Fix Minimal BASH like line editing is supported GRUB Error In Linux]("https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/")" ([How to Fix Minimal BASH Like Line Editing is Supported GRUB Error In Linux?]("https://www.geeksforgeeks.org/how-to-fix-minimal-bash-like-line-editing-is-supported-grub-error-in-linux/") didnt work either) and had tried boot-repair, for the link to pastebin I took a photo from the screen.

And as you say, clone copied the UUID of the old Ubuntu partition  (sdc1): e4c6b602-f598-49d9-b6ee-809c01de1c13 to the new Ubuntu partition  (sdd2). 

```
NAME   FSTYPE   UUID                                 PARTUUID                             LABEL             PARTLABEL
sda                                                                                                         
&#9500;&#9472;sda1 ntfs     2AC8BC64C8BC2FC5                     72b63971-b1b4-11ed-84c4-74d4358257f8 System-reserviert 
&#9500;&#9472;sda2 ntfs     A466BE2966BDFC5C                     72b63972-b1b4-11ed-84c4-74d4358257f8                   
&#9500;&#9472;sda3 vfat     98C7-63A0                            72b63973-b1b4-11ed-84c4-74d4358257f8                   
&#9492;&#9472;sda4 ntfs     40A664CBA664C350                     72b63974-b1b4-11ed-84c4-74d4358257f8                   
sdb                                                                                                         
&#9492;&#9472;sdb1 ntfs     195CC83A2368BEA1                     b6ed9533-01                          BACKUP            
sdc                                                                                                         
&#9492;&#9472;sdc1 ext4     e4c6b602-f598-49d9-b6ee-809c01de1c13 fb7d13f7-bbba-4079-800d-70f58a00141e                   
sdd                                                                                                         
&#9500;&#9472;sdd1 vfat     6374-DAD9                            1502bf42-5e30-41d1-b18a-0538b439b920                   
&#9500;&#9472;sdd2 ext4     e4c6b602-f598-49d9-b6ee-809c01de1c13 5f94c848-6abf-4af9-a3b3-2d6138730a74                   
&#9492;&#9472;sdd3 ntfs     DA44FAD944FAB77B                     b8e27158-1179-4681-a89c-0840044d1634 1TB               1TB-FAT32
sde                                                                                                         
&#9492;&#9472;sde1 vfat     B815-7D03                             71b9534a-7657-4a0d-80e1-4b9ee61c51bc UBUNTU 22_0       Main Data  Partition
```

> **MAFoElffen said:**
> :...I've done my part. sorry, I didnt know that this GUI Grub Customizer were a No-Go :sad:
The format of the sdd3 to ntfs was no problem at all. I did it in Windows, before any use of this 1TB partition. 
But I dont understand, how *you* made it to NOT get the same partition UUIDs when cloning your VMs!?

 > **oldfred said:**
> ...Please review my first post where I said  install works and some image type copies can take days to  resolve... you are right, it could have been faster if I installed fresh  and copied all data later and installed all app etc. etc. but first is  the hope that clone works :wink: and after all, it is experience what I win here. And since yet I lost nothing but time :smile:

So now, do I need to change the UUID  (e4c6b602-f598-49d9-b6ee-809c01de1c13) of sdd2 manually and put it in  the grub config (of grub in sda3 and sdd1)?
I have the impression that I start walking on thin ice :wink:

PS.: is there a way, to set the auto-logout time in ubuntuforums.org any longer? I am always logged out after a very short time, it is a bit annoying. But I dont find a setting in my profile to set keep logged in time e.g. 1 day or so.

---

### Post by francwalter on 2023-10-25
After a while of search:
Will the following code (inside old Ubuntu on sdc1) do the trick?
```
#sudo tune2fs -U random /dev/sdd2
#sudo update-grub


```
And  then, I would be able to boot to the new (cloned, sdd2) Ubuntu with  grub boot loader of the older Ubuntu (on sda3) and once in the new  Ubuntu on sdd2 I do there udate-grub as well (without tune2fs!)?
Or do I still misunderstand the whole grub thing?

I  looked into /boot/grub/grub.cfg (on old sdc1-Ubuntu, with cat/less) and  found the old UUID very often, impossible to change here something.

```
#sudo lsblk -o NAME,UUID,PARTUUID
NAME   UUID                                 PARTUUID
loop0                                       
loop1      
...
loop63                                      
loop64                                      
sda                                         
&#9500;&#9472;sda1 2AC8BC64C8BC2FC5                     72b63971-b1b4-11ed-84c4-74d4358257f8
&#9500;&#9472;sda2 A466BE2966BDFC5C                     72b63972-b1b4-11ed-84c4-74d4358257f8
&#9500;&#9472;sda3 98C7-63A0                            72b63973-b1b4-11ed-84c4-74d4358257f8
&#9492;&#9472;sda4 40A664CBA664C350                     72b63974-b1b4-11ed-84c4-74d4358257f8
sdb                                         
&#9492;&#9472;sdb1 195CC83A2368BEA1                     b6ed9533-01
sdc                                         
&#9492;&#9472;sdc1 e4c6b602-f598-49d9-b6ee-809c01de1c13 fb7d13f7-bbba-4079-800d-70f58a00141e
sdd                                         
&#9500;&#9472;sdd1 6374-DAD9                            1502bf42-5e30-41d1-b18a-0538b439b920
&#9500;&#9472;sdd2 e4c6b602-f598-49d9-b6ee-809c01de1c13 5f94c848-6abf-4af9-a3b3-2d6138730a74
&#9492;&#9472;sdd3 DA44FAD944FAB77B                     b8e27158-1179-4681-a89c-0840044d1634
sr0
#lsblk -fs
NAME   FSTYPE   FSVER LABEL             UUID                                 FSAVAIL FSUSE% MOUNTPOINTS
loop0  squashfs 4.0                                                                0   100% /snap/android-studio/127
...
loop63 squashfs 4.0                                                                0   100% /snap/wine-platform-runtime-core20/82
loop64 squashfs 4.0                                                                0   100% /snap/wine-platform-runtime-core20/83
sda1   ntfs           System-reserviert 2AC8BC64C8BC2FC5                                    
&#9492;&#9472;sda                                                                                       
sda2   ntfs                             A466BE2966BDFC5C                                    
&#9492;&#9472;sda                                                                                       
sda3   vfat     FAT32                   98C7-63A0                              60,2M    37% /boot/efi
&#9492;&#9472;sda                                                                                       
sda4   ntfs                             40A664CBA664C350                                    
&#9492;&#9472;sda                                                                                       
sdb1   ntfs           BACKUP            195CC83A2368BEA1                                    
&#9492;&#9472;sdb                                                                                       
sdc1   ext4     1.0                     e4c6b602-f598-49d9-b6ee-809c01de1c13    160G    51% /
&#9492;&#9472;sdc                                                                                       
sdd1   vfat     FAT32                   6374-DAD9                                           
&#9492;&#9472;sdd                                                                                       
sdd2   ext4     1.0                     e4c6b602-f598-49d9-b6ee-809c01de1c13                
&#9492;&#9472;sdd                                                                                       
sdd3   ntfs           1TB               DA44FAD944FAB77B                                    
&#9492;&#9472;sdd                                                                                       
sr0

```
But I have not yet understood the difference between UUID and PARTUUID, why two? UUID is different for sdd1, sdd2 and sdd3 so it is already a kind of partition uuid, isntit?

---

### Post by oldfred on 2023-10-25
PartUUID is the GUID of gpt partitions. GUID also has type UUIDs and other better features over the very old MBR.
MBR(msdos) does not really have a partUUID, but UEFI uses parttype to know which is the ESP. 
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

When we set a esp flag with gparted or ef00 with gdisk, we really are setting the very long parttype.
lsblk -o +label,PARTLABEL,parttype

You need to update fstab before you update grub.
There may be some other places also, but that should give you a working system. But later any errors on UUIDs are probably from another setting.

---

### Post by francwalter on 2023-10-25
> **oldfred said:**
> ...You need to update fstab before you update grub...
OK then, I will do [B][I]sudo tune2fs -U random /dev/sdd2
[/I][/B]Then I change the UUID of sdd2 in sdd2's fstab too.
Is it better to do all this from a Live Ubuntu or better in my old Ubuntu (on sdc1)?

---

### Post by oldfred on 2023-10-25
Use whatever Ubuntu boots and allows you to mount & edit fstab.
You have to chroot into your broken install to run commands there, or use Boot-Repair to update grub.
Boot-Repair's advanced mode does a minimal chroot as it has mounted some partitions and then has you copy commands into terminal.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

---

### Post by francwalter on 2023-10-25
[Boot Info summary on pastebin]("https://paste.ubuntu.com/p/xVbv6h6TNM/")

```

$ sudo e2fsck -f /dev/sdd2
e2fsck 1.46.5 (30-Dec-2021)
Durchgang 1: Inodes, Blöcke und Größen werden geprüft
Durchgang 2: Verzeichnisstruktur wird geprüft
Durchgang 3: Verzeichnisverknüpfungen werden geprüft
Durchgang 4: Referenzzähler werden überprüft
Durchgang 5: Zusammengefasste Gruppeninformation wird geprüft
/dev/sdd2: 1259694/62480384 Dateien (1.9% nicht zusammenhängend), 53204577/249912064 Blöcke

$ sudo tune2fs -U random /dev/sdd2
tune2fs 1.46.5 (30-Dec-2021)
Festlegen der UUID auf diesem Dateisystem kann einige Zeit benötigen.
Trotzdem weitermachen (oder warte 5 Sekunden zum weitermachen) ? (y,N) <Verarbeitung läuft

$sudo lsblk -o NAME,UUID,PARTUUID
NAME UUID PARTUUID
loop0
...
loop10                                      

sda                                         
&#9500;&#9472;sda1 2AC8BC64C8BC2FC5                     72b63971-b1b4-11ed-84c4-74d4358257f8
&#9500;&#9472;sda2 A466BE2966BDFC5C                     72b63972-b1b4-11ed-84c4-74d4358257f8
&#9500;&#9472;sda3 98C7-63A0                            72b63973-b1b4-11ed-84c4-74d4358257f8
&#9492;&#9472;sda4 40A664CBA664C350                     72b63974-b1b4-11ed-84c4-74d4358257f8
sdb                                         
&#9492;&#9472;sdb1 195CC83A2368BEA1                     b6ed9533-01
sdc                                         
&#9492;&#9472;sdc1 e4c6b602-f598-49d9-b6ee-809c01de1c13 fb7d13f7-bbba-4079-800d-70f58a00141e
sdd                                         
&#9500;&#9472;sdd1 6374-DAD9                            1502bf42-5e30-41d1-b18a-0538b439b920
&#9500;&#9472;sdd2 134dde81-df92-4bcf-b024-93745c0457b1 5f94c848-6abf-4af9-a3b3-2d6138730a74
&#9492;&#9472;sdd3 DA44FAD944FAB77B                     b8e27158-1179-4681-a89c-0840044d1634
sde                                         
&#9492;&#9472;sde1 B815-7D03                            71b9534a-7657-4a0d-80e1-4b9ee61c51bc
sr0

```

OK then, now /dev/sdd2 has the UUID: **134dde81-df92-4bcf-b024-93745c0457b1**
Now fstab:
```
$sudo mount
...
/dev/sdd2 on /media/ubuntu/134dde81-df92-4bcf-b024-93745c0457b1 type ext4 (rw,nosuid,nodev,relatime,errors=remount-ro,uhelper=udisks2)

$sudo vi /media/ubuntu/134dde81-df92-4bcf-b024-93745c0457b1/fstab
(changing e4c6b602-f598-49d9-b6ee-809c01de1c13 to 134dde81-df92-4bcf-b024-93745c0457b1)

$cat /media/ubuntu/134dde81-df92-4bcf-b024-93745c0457b1/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#  
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc1 during installation
# fcw: vorher: UUID=e4c6b602-f598-49d9-b6ee-809c01de1c13 /               ext4    errors=remount-ro 0       1
UUID=134dde81-df92-4bcf-b024-93745c0457b1 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda3 during installation
#UUID=98C7-63A0  /boot/efi       vfat    umask=0077      0       1
/swapfile none swap sw 0 0
# 2023-03-09 NAS einhaengen, login ist in: ~/.smbcredentials
//192.168.0.100/share /mnt/nas cifs vers=1.0,credentials=/home/f/.smbcredentials

UUID=6374-DAD9  /boot/efi       vfat    defaults      0       1

```
Now boot-repair...

---

### Post by francwalter on 2023-10-25
> Während der Reparatur ist ein Fehler aufgetreten.
Error: NVram is locked (Ubuntu not found in efibootmgr). Bitte melden Sie diese Nachricht an [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

Bitte auf ein Papier die folgende Adresse notieren:
[https://paste.ubuntu.com/p/Dw5zfwNytJ/](https://paste.ubuntu.com/p/Dw5zfwNytJ/)

Falls Sie ein Startproblem haben, geben Sie hier diese Adresse an:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] 

Locked-NVram entdeckt. Bitte SecureBoot im BIOS deaktivieren. Versuchen Sie es dann erneut.

Same error as before reported. Will try now again to boot my new Ubuntu...
... Nope, still shows entry Ubuntu on /sdd2 but boots then old Ubuntu on /sdc1 :(
```
$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-35-generic
Found initrd image: /boot/initrd.img-6.2.0-35-generic
Found linux image: /boot/vmlinuz-6.2.0-34-generic
Found initrd image: /boot/initrd.img-6.2.0-34-generic
Found linux image: /boot/vmlinuz-5.19.0-46-generic
Found initrd image: /boot/initrd.img-5.19.0-46-generic
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda3@/EFI/Microsoft/Boot/bootmgfw.efi
Found Ubuntu 22.04.3 LTS (22.04) on /dev/sdd2
Adding boot menu entry for UEFI Firmware Settings ...
done
```

---

### Post by francwalter on 2023-10-25
This is my old Ubuntu's [/boot/grub/grub.cfg on Pastebin]("https://paste.ubuntu.com/p/F2p9fyB9w4/")  

I can read the new Ubuntu's UUID in its menu entry:
```
...
menuentry 'Ubuntu 22.04.3 LTS (22.04) (on /dev/sdd2)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-134dde81-df92-4bcf-b024-93745c0457b1' {
    insmod part_gpt
    insmod ext2
    set root='hd3,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd3,gpt2 --hint-efi=hd3,gpt2 --hint-baremetal=ahci3,gpt2  134dde81-df92-4bcf-b024-93745c0457b1
    else
      search --no-floppy --fs-uuid --set=root 134dde81-df92-4bcf-b024-93745c0457b1
    fi
    linux /boot/vmlinuz-6.2.0-35-generic root=UUID=e4c6b602-f598-49d9-b6ee-809c01de1c13 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-6.2.0-35-generic
}
...
```
But still I see there also: ***root=UUID=e4c6b602-f598-49d9-b6ee-809c01de1c13*** 
Shouldnt it be: ***root=UUID=134dde81-df92-4bcf-b024-93745c0457b1***

So maybe I just edit /boot/grub/grub.cfg and change that UUID to the new one? I am a bit afraid about the "DO NOT EDIT THIS FILE" in the beginning of grub.cfg :(
But boot-repair didnt fix (change) it and neither did update-grub.

---

### Post by MAFoElffen on 2023-10-25
Hint to others. 

Remove or unplug all drives except the target drive with the new EFI. Boot off it. Reinstall grub. Shutdown.

Reconnect ervrything. Check the boot order in UEFI BIOS. Boot from EFI boot to the new EFI partition. Ensure you are on the new Ubuntu install. Update grub, so that OS_Prober searches for and adds the other OS'es.

---

### Post by oldfred on 2023-10-25
Do you have a separate /boot partition. Then UUIDs are different.
But separate /boot not often used with desktops, more with server type installs with LVM or other configurations.

---

### Post by francwalter on 2023-10-25
**TADAAAA!!!**

Got it :) :) :)

(writing this post from /sdd2)

Thank you olfred and MAFoElffen for your continous help and that you didnt give up on me :)

So, what did I do in the end?

I changed the UUID with tune2fs to random.
Then I looked it up with lsblk and wrote it in fstab of the new Ubuntu (/sdd2).
After that I tried boot-repair but this didn't work completely and update-grub neither. I had still some entries with the old UUID in my grub.cfg for the /sdd2 boot menu. So first I changed only one of them with the hated and detested Grub Customizer (I was too anxious to edit grub.cfg manually), which was easy enough. Saved it, boot and voila! That entry that I fixed, booted into my /sdd2 Ubuntu!
There (in /sdd2) I ran update-grub which fixed this time for good all wrong UUIDs and even in the grub.cfg of the old /sdc1 Ubuntu too. Good work, update-grub, good work ;)
I went back a last time to /sdc1 Ubuntu to check the grub.cfg but it was all done :)

My steps are all in much more details in this thread above, so I keep that short here in my last post.

But now: with SSD it is a difference like day and night! Boot up to work state in some 30 seconds maybe, on HDD this was about 15 minutes till the HDD stopped the continous spinning and searching with its typical noises! Here on SSD it is totally quiet! And fast! 
It was all worth it!
I will do backup now with rsync or such from new Ubuntu to old Ubuntu (with anacron maybe) and check from time to time, if old Ubuntu still works and has updated files and folders etc.

OK then :)
Thank.frank

---

### Post by oldfred on 2023-10-25
Glad you got it working.

Please change to solved. Others may then find thread.

---

### Post by francwalter on 2023-10-28
Hello, sorry to bother again, a question arise after some days, I hope somebody reads this despite the thread is "solved" already:

I have now grub on both, on /sdc1 (hdd from old Ubuntu) and on /sdd2 (ssd from new, cloned Ubuntu).
Bootloaders are on /sda3 (for grub on /sdc1) and on /sdd1 (for grub on /sdd2).

I have set the boot sequence in Bios to boot from /sdd (where the new Ubuntu is on /sdd2). But the bootlaoder is always from /sda3 (so it loads grub.cfg from /sdc1).
I tested it, I have set a different text for the two different grub, and always it loads the grub from /sdc1). 

So the bootloader is selected from the /sda3 efi partition, even if I set in Bios (F11, boot options) to boot from /sdd disk.
Shouldnt the bootloader from /sdd1 be used, to start grub in /sdd2 when I select /sdd in Bios boot selection?

I do not understand that. Did I still have a mistake in my configuration then?
It is not a big deal, if I boot the new Ubuntu on /sdd2 with grub from /sdc1 but I would like to understand, why it does not boot with grub from /sdd1 when I select /sdd in Bios boot device.
I ran again update-grub in the new Ubuntu (/sdd2) without changes and errors.

Any hints? Thanks.

---

### Post by oldfred on 2023-10-28
You can run Boot-Repair and in its report will be all the details of your boots.
You have to first look at UEFI entries which use GUID/partUUID to find ESP.
Then in each ESP will be a 3 line grub.cfg that boots (configfile) using UUID to find the full grub.cfg in your install.
If you still have a duplicate UUID that can confuse things.

---

### Post by francwalter on 2023-10-28
Indeed! In line 1748 in my [boot-repair report]("https://paste.ubuntu.com/p/j2cmkXQFTs/") (on pastebin, or [mine]("https://paste.ubuntu.com/p/WW2JdNYgKq/")),
which I just did again with USB Flash Drive Ubuntu 22.04.03 I can read:

```

===================== sdd1/efi/ubuntu/grub.cfg (filtered) ======================
search.fs_uuid e4c6b602-f598-49d9-b6ee-809c01de1c13 root hd3,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```
and this UUID is from my old Ubuntu (efi in /sda3, grub and Ubuntu on /sdc1).It should be here the UUID from /sdd2, I guess.
The 3 lines to find the full grub.cfg :(
So I have to edit /sdd1/efi/ubuntu/grub.cfg, should be 
134dde81-df92-4bcf-b024-93745c0457b1

So I did change that file:

```
sudo mount /dev/sdd1 /mnt
sudo vi /mnt/EFI/ubuntu/grub.cfg (changed ***e4c6b602-f598-49d9-b6ee-809c01de1c13*** for [B][I]134dde81-df92-4bcf-b024-93745c0457b1
[/I][/B]ubuntu@ubuntu:/mnt/EFI/ubuntu$ cat grub.cfg 

search.fs_uuid 134dde81-df92-4bcf-b024-93745c0457b1 root hd3,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

cd /
sudo umount /dev/sdd1
reboot
```
and now I reboot...
... and Tadaa, grub from /sdd2 is working :)
Thanks.

EDIT: and now, after only some months, the new Fanxiang SSD (sdd) seems broken, see my post in a german [Ubuntu auf SSD wirft Fehler und startet nicht mehr]("https://forum.ubuntuusers.de/topic/ubuntu-auf-ssd-wirft-fehler-und-startet-nicht-/#post-9413627")   :( :( :(

---

