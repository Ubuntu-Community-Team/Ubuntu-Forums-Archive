---
title: "Cannot install Ubuntu"
date: 2013-11-14
forum: Installation &amp; Upgrades
---

### Post by vincent.andrew.1 on 2013-11-14
I am also new to Linux and am running into same issue - I think - I was able to run the live cd, which work fantastic.  I then tried to install - with a complete wipe of my windows 8 OS since I do not want it on my computer and it got hung up about 1/2 through the process with a ubuntu screen with the spinning "wait" symbol all night (I got tired and went to bed and it was still there in the AM).

I am running a newly built PC with the following 

- Gigabyte GA-F2a85xm-hd3 AMD A85 (hudson D4) motherboard
- AMD A4-5300 Trinity APU @ 3.4 GHz w Direct X AMD Redeon HD 7480D (this is where I think the issue is, with the video processor)
- 16 GB SDRAM
- Plenty of room on two hard drives
     - 1 TB
     - 320 GB

I can restart and get into the boot menu and choose the DVD - then I get into the installation menu and can hit "F6" but when I try to select "nomodset" I can not seem to get it to bo beyond allowing me to check off the "nomdset" option.  I have been at work all day - and computer is at home so I can not try anything right now - but I found some free time to do some research and located this thread.

Did this fix work for "sunnysanchit99" ???  I will check thread tomorrow and see if there is any advice and try again.  

To be honest I am in law enforcement and do not have any programming background but I love to tinker with this stuff and get around fairly well so I am willing to try - relying on forums for help.  I have been doing the same with android for a few years now and have had great success (with only one brick...).

Thanks
Newbie

---

### Post by heir4c on 2013-11-14
If you hit F6 than you select nomodeset and use the space bar to check it. Than click Enter.

Maybe you can try the latest Ubuntu version 13.10.

---

### Post by fantab on 2013-11-15
Have you successfully removed Windows 8?
How were you booting Windows 8? Was it a UEFI boot or 'Legacy/MBR' boot?
If you are not sure how to answer the second and third Question, boot with Ubuntu DVD/USb - 'Try Ubuntu Without Installing', open Terminal [Ctrl+Alt+T], run the following commands and post their respective output here:

```
sudo parted -l
sudo fdisk -l
```

**[This Thread]("http://ubuntuforums.org/showthread.php?t=1613132")** has excellent information about using NOMODESET options, read through it.

A piece of advice: If this is the first time you will be using a Linux OS then I suggest you keep Windows and dual boot with Ubuntu. Don't use Windows but keep it. The point is there are certain Windows applications and games that you may be used to and may find it difficult to find a suitable alternative to such in Linux. Linux beginner often gets frustrated with Linux when they face such niggling issues. Also most of the hardware manufacturers out there test their hardware on Windows and release their drivers only for Windows. Let me also tell you, in the same breath, that most of the hardware out there works in Linux, however there are certain instances where things get frustrating. So until such time that you are perfectly comfortable with Linux/Ubuntu keep Windows OS around.

---

### Post by vincent.andrew.1 on 2013-11-15
#2 - I tried "enter" and the computer became unresponsive.

#3 - I should have mentioned this in post - windows was a UEFI boot but BIOS allows both legacy and UEFI boots and I have it set to allow both.  Should I adjust it to run just legacy?  
I think I will follow your advice and install windows again although the computer is mainly for browsing / music / photos and Ubuntu seems to cover all that.  I had windows 8 on it but never activated it since I do not have a code - would an older version of windows work better w dual boot?  Will windows 8 work with legacy boot?

Thanks for the responses and the help.

---

### Post by fantab on 2013-11-15
We can dual-boot with any version of Windows, since XP [Don't know about earlier versions]. 

Yes, Win8 will work in Legacy mode. 
Since you don't have the 'activation code'  and if you are planning to pay for it, then you can ignore my advice, unless offcourse you want to. I don't see a point in paying for it, if you think Ubuntu can take care of your needs. With the kind of needs you mention, Ubuntu will serve you good.

I would suggest that you use UEFI as it is the new standard and the future. Legacy BIOS will be eventually phased out. So I don't see a point in NOT using UEFI when you have it.

> #2 - I tried "enter" and the computer became unresponsive.
You need to elaborate on that.

---

### Post by vincent.andrew.1 on 2013-11-15
It just froze and did not do anything - I will try again. 

I thought I needed to use Legacy for Linux - was I mistaken?

---

### Post by fantab on 2013-11-15
> **vincent.andrew.1 said:**
> It just froze and did not do anything - I will try again. 

I thought I needed to use Legacy for Linux - was I mistaken?

Do you still have Windows on the machine?
Do you want to keep it or Remove it?
From BIOS Switch to UEFI mode.
This should guide you with your Ubuntu install in UEFI mode: [https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode)

But before you Install ubuntu, Boot your Ubuntu DVD/USB and 'Try Ubuntu without intalling', when the desktop is ready, Open Terminal [Ctrl+Alt+T], run the following commands and post its output here:
```
sudo parted -l
sudo fdisk -l
```

Lets see if you Hard disk is set for UEFI or Legacy.

---

### Post by vincent.andrew.1 on 2013-11-15
I was just looking into the motherboard and found this on the manufacturers website


[LIST=1][COLOR=red]
[*]Due to different Linux support condition provided by chipset vendors, please download Linux driver from chipset vendors' website or 3rd party website.[/COLOR]
[/LIST]

So my chipset is the AMD A85X and I have found this driver

[AMD Catalyst&#8482; 13.4 Proprietary Linux x86 Display Driver]("http://www2.ati.com/drivers/linux/amd-driver-installer-catalyst-13-4-linux-x86.x86_64.zip")

on AMD's website - am I on the right path here?  If I do not have a functioning OS how to I install the driver?  Through the Motherboard set-up?

Thanks

---

### Post by vincent.andrew.1 on 2013-11-15
Out of time for now - I will be back....

---

### Post by fantab on 2013-11-15
Don't worry, Ubuntu will provide the necessary drivers via 'Additional Drivers' from the application 'Software & Updates'.
[http://ubuntuforums.org/showthread.php?t=2027920&p=12821707#post12821707](http://ubuntuforums.org/showthread.php?t=2027920&p=12821707#post12821707)

First of all you need to install Ubuntu. Reply to my questions in my earlier post, and we will guide you through the install. Also post the output of the commands as requested.

---

### Post by vincent.andrew.1 on 2013-11-17
Reply to "parted" command

Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  316MB   315MB   ntfs         Basic data partition          hidden, diag
 2      316MB   419MB   104MB   fat32        EFI system partition          boot
 3      419MB   554MB   134MB                Microsoft reserved partition  msftres
 4      554MB   1000GB  1000GB  ntfs         Basic data partition          msftdata


Model: ATA Hitachi HDT72503 (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  304GB  304GB   primary   ext4
 2      304GB   320GB  16.3GB  extended
 5      304GB   320GB  16.3GB  logical   linux-swap(v1)


Model: Hitachi HDS721050CLA362 (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ntfs


Model: ST94813A  (scsi)
Disk /dev/sde: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  34.4GB  34.4GB  primary  fat32        boot, lba


Model: HL-DT-ST DVD+-RW GSA-H73N (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac

Number  Start   End     Size    File system  Name   Flags
 1      8192B   24.6kB  16.4kB               Apple
 2      3669MB  3678MB  9306kB               EFI

Reply ro "fdisk" command

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d156f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   593268735   296633344   83  Linux
/dev/sdb2       593270782   625141759    15935489    5  Extended
/dev/sdb5       593270784   625141759    15935488   82  Linux swap / Solaris

Disk /dev/sdd: 499.6 GB, 499635978240 bytes
255 heads, 63 sectors/track, 60743 cylinders, total 975851520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x01c613fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   975836294   487918116    7  HPFS/NTFS/exFAT

Disk /dev/sde: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x278e6a65

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048    67110911    33554432    c  W95 FAT32 (LBA)

The last two drives are external storage for media - the 1 TB is the new drive and the 320 GB is the drive from my old set up.  I tried installing on the 320 initially - should I try the 1 TB?

---

### Post by oldfred on 2013-11-17
While you can have Windows with UEFI and Ubuntu with BIOS boot it is a bit of a hassle as you have to go into UEFI/BIOS and turn it on of off and choose  system that matches each time. UEFI and BIOS are not compatible, so once you start booting in one mode you cannot switch, or from grub menu boot another system that is not in the same boot mode you started with.

Since Windows is UEFI, it would then be best to install Ubuntu in UEFI also. And now that main drive is gpt, you should partition all new drives as gpt so you will not have the above boot issue.


 I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

I would also suggest an efi partition at the beginning of every drive. Then you could make that drive bootable without the others. But you can install grub2's efi boot files in the Windows efi partition or both. 

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

I would also shrink your very large NTFS Windows system partition and make the rest of drive a NTFS data partition. You still should not have fast boot or hibernation on, but writing into the main Windows system partition can lead to issues. Setting system partition read only by default and a shared NTFS partition as read/write may reduce issues.

Some examples of users that installed into second drives are in links in my signature.

---

### Post by fantab on 2013-11-17
Your 'New 1TB' HDD has GUID Partition Table [**GPT**], and this came pre-installed with Windows8. 
From GPT Windows can ONLY boot in (U)EFI mode. While Ubuntu/Linux can boot in both UEFI and 'Legacy/MBR' mode.
Since Win8 came preinstalled and that we can see a FAT32 EFI partition you have UEFI boot Enabled. And Windows is booting in UEFI mode.

The best thing to do will be to install Ubuntu too in UEFI mode.

Wheras the older 320GB HDD has the legacy '**msdos**' Partition Table. From this type of Partition Table, both Ubuntu and Windows, can ONLY boot in 'Legacy/MBR' mode. No UEFI booting.

If you want to install Ubuntu on the 320GB HDD then you will have convert the HDD from 'msdos' to 'GPT', this you can do quite easily with Gparted (available on Ubuntu install medium).
In GPT formatted disks you can have upto 100 or more Primary Partitions, unlike 'msdos' formatted disks where you can ONLY have FOUR Primary Partitions. And to overcome this we use Extended Partition. So in GPT Hdd you don't need an Extended Partition.
To boot from GPT in EFI mode you will need to create a separate 300Mb FAT32 Partition with a 'boot' flag, the following is the suggested partition on GPT HDD:
> 300Mb Primary FAT32 'boot flag' #EFI Partition
25GB Primary EXT4  / #Ubuntu system files
25GB Primary EXT4 Free
4GB Primary SWAP
All the remaining GB Primary EXT4 /home or a simple DATA Partition.

Warning: Deleting/Changing Partition table WILL result in definite data loss. BACKUP your Important DATA before.

To convert the Partition Table to GPT, open Gparted, after booting Ubuntu DVD/USB with 'Try Without Installing' Option.
In Gparted select your 320GB HDD [/dev/sdb], and from the top menu choose 'Devices' and select 'Create New Partition Table', to select GPT use 'Advanced' settings. After changing HDD to GPT recreate partitions as suggested.

REBOOT.

Boot Ubuntu DVD/USB in EFI mode, this is important if you want to install in UEFI mode. [See Instructions here]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode"). 
Install using 'Something Else' Option and manually tell Ubuntu where to install, if you leave to default installer then it will install to /dev/sda 1TB hdd.
Install GRUB to /dev/sdb.

EDIT: oldfred beat me to it :)

---

### Post by vincent.andrew.1 on 2013-11-17
Thank you both. 

Between my post and your responses I tried the live CD again but this time I ran it in UEFI instead of legacy. I then installed from the live CD onto the 1 TB drive and it was successful. So problem solved.

But now I would like to format my 320 GB drive and can not seem to do so since that is where I tried to install Ubuntu last time and it is telling me I am not the owner. I think the answer is in fantabs post.

---

### Post by fantab on 2013-11-17
> **vincent.andrew.1 said:**
> Thank you both. 

Between my post and your responses I tried the live CD again but this time I ran it in UEFI instead of legacy. I then installed from the live CD onto the 1 TB drive and it was successful. So problem solved.

But now I would like to format my 320 GB drive and can not seem to do so since that is where I tried to install Ubuntu last time and it is telling me I am not the owner. I think the answer is in fantabs post.

First of all, Congrats!

Did you try to format the HDD from installed Ubuntu or Live Ubuntu?

---

### Post by vincent.andrew.1 on 2013-11-17
From the installed version.  The disks properties tell mer "root" is the owner.

---

### Post by oldfred on 2013-11-17
If linux formated, you need to set ownership & permissions with chown & chmod. Unmount first if auto mounted by Nautilus, so you can manually remount.
If it was an old install, it may be easier to recreate it first as it is full of Ubuntu system files. If you just want a data partition, you would want to delete all those. Reformatted would be the quickest way to delete everything.

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

If a permanent drive that will always be mounted you will want to add it to fstab. Then on reboots it is always mounted.
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

---

### Post by vincent.andrew.1 on 2013-11-17
Thank you both - I really appreciate it - some of what you are saying is starting to make sense but I am a cop with no programming back ground so some of this is a bit above my level of understanding, but I am catching on and I can follow directions.
My goal is to have the the 1 TB drive as my main drive and to use the 320 GB drive merely for storage - docs / music / etc...
I bought the 1 TB for this build and had the 320 GB from the old build.  Unfortunately I did try to instal Linux on the 320 initially since windows was on 1 TB - but now windows is gone.  
If I understand oldfred correctly following his instructions will get me to my goal, of having the 320 drive merely as a data storage device - correct?

I am stuck at work this evening and tomorrow so I can try this tomorrow afternoon / evening.

Thanks again.

---

### Post by oldfred on 2013-11-17
Should work. But again it may be better to make drives gpt since new main drive is gpt partitioned. If later you want to change it could require total reformat. But there are some conversion tools.

I actually like to make every hard drive a bootable drive.

I follow this logic but use Ubuntu.
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by vincent.andrew.1 on 2013-11-18
I am good to go with OS and hard drive - thank you guys!  This thread can be marked "solved".

One last question - should I be getting the ubuntu grub menu when the computer boots or should it go right to ubuntu?  I am getting the grub menu.

---

### Post by Iowan on 2013-11-18
> **vincent.andrew.1 said:**
>  This thread can be marked "solved".
Go for it!
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by fantab on 2013-11-18
> **vincent.andrew.1 said:**
> I am good to go with OS and hard drive - thank you guys!  This thread can be marked "solved".

One last question - should I be getting the ubuntu grub menu when the computer boots or should it go right to ubuntu?  I am getting the grub menu.

YES, you will get Grub Menu, since you are dual-booting. However, by default, the Grub Menu will show for 10 seconds. 
You can easily reduce this time by editing /etc/default/grub file:

From Terminal:
```
sudo cp /etc/default/grub /etc/default/grub.bak
sudo gedit /etc/default/grub
```

The first command will save your current /etc/default/grub as backup, grub.bak
The second command will open the /etc/default/grub file in 'gedit', text-editor.

When the file is open look for the line:
GRUB_TIMEOUT=**10**
chnage the above **10 seconds** to whatever suits you, just DON'T make it ZERO. I have this set to 3.
Save the file and run the following command:

```
sudo update-grub
```.

---

### Post by vincent.andrew.1 on 2013-11-18
I guess I didn't realize I could mark it solved - I will take care of that. 

My system is not a dual boot - I only have Ubuntu on it so i I thought it would go right to it. I will change the time but it would be great to skip grub.

---

### Post by fantab on 2013-11-18
Ah.. In that case you have to 'uncomment' (remove **#** from in front of the line) this line in /etc/default/grub:

**#**GRUB_HIDDEN_TIMEOUT=0 change this to
GRUB_HIDDEN_TIMEOUT=0

More Details:
[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

---

### Post by vincent.andrew.1 on 2013-11-30
fantab

I finally tried to change the timeout on the grub menu but when the editor opens the file is "read only" and I can not save any changes I make.  Suggestions

In the terminal I get this response

** (gedit:2750): WARNING **: Could not load Gedit repository: Typelib file for namespace 'GtkSource', version '3.0' not found



Andy

---

### Post by oldfred on 2013-11-30
You may get errors like that if you use a graphic application with sudo.
Better to use gksudo if gui app.

gksudo gedit /etc/default/grub

Then after any grub configuration file edit. (not a gui app).
sudo update-grub

Sometimes when I type a command it comes back with a permissions type error or just nothing. So then I know I needed sudo and try again. And then when it comes back with the above error I know I should not use sudo but gksudo or gksu. And sometimes that is the only way I know because I really do not remember which is which on sudo or gksu.  Maybe the old in oldfred? :)

---

### Post by fantab on 2013-11-30
Lets use the Terminal-based text editor, Nano. I don't know what version of Ubuntu you have, but 'gksudo' is NOT installed by default in 13.10. Nano is simple and with it we can open the file in Terminal.

```
sudo nano /etc/default/grub
```

You have to save the file after editing it... [Nano usage]("http://www.gentoo.org/doc/en/nano-basics-guide.xml").

---

