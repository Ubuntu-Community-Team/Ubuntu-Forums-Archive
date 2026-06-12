---
title: "Installing Ubuntu on 60GB SSD and storing all personal files on 1TB HDD?"
date: 2015-05-05
forum: Installation &amp; Upgrades
---

### Post by G33shooter on 2015-05-05
Hello,

I am building my first computer and would like to have Ubuntu on a dedicated 60GB SSD while saving all my personal files to a separate 1TB HDD.  I am assuming, during installation, I would need to be the one to fiddle around with partitions to get this setup to work correctly, right?  If so, would I need to partition the SSD?  I have 8GB RAM, so would I do one partition for swap (16GB?) then one partition for / (44GB?), would I need to do a partition for /home on the SSD? On the 1TB HDD would I do a single partition of 1TB for /home?  then click continue and all is gravy? Or not so much?

If I did the setup as mentioned, when saving a document, I would click "save" then click on the 1TB drive and choose the folder to drop the file in?  If this is the case, is there a way to click "save" choose the folder I want to save the file to, and have it automatically saved to that file on the 1TB HDD without using up space on the 60GB SSD?

any advice would be greatly appreciated!

Thank you all very much!

---

### Post by etescartz on 2015-05-05
Hi! I've been through this debate myself , and for I feel I can share some of my thoughts on your scenario.You should only be concerned with this type of partitioning , only if you dualboot. But as I understand this is a Ubuntu only install.

Using a SSD gives your system faster/shorter boot times.But if you want all your installed applications and software ,even the desktop environment , to take advantage of the SSD's speed , you'll probably want to configure your /home partition also on the SSD.

My advice to you is to keep things simple as you probably will reinstall or upgrade the system many times. Just experiment with things and make sure that your important data isn't stored on the disks before you're formating them. It is best to always have a second backup somewhere else.

Proposal 1: (enhanced performance)
Select manual partioning and then 
SSD\
      Select this disk as root / partition and Ubuntu will automatically partition the disk for you).
HDD\
Format this disk as one whole EXT4 partition and select a name for it.( Please be aware that you should set up a mount point for it under /media | Just select the custom mount point option and type the folder path for it , by yourself. Make it something like /media/storage or /media/files or something else you would prefer)
     That will tell Ubuntu to mount it at boot. You'll be able create separate folders for your files afterwards.


Proposal 2: (User's files are kept on a separate disk from the disk that the OS is on)
SSD\
      Select manual partitioning and use SSD as root / partition like in the previous example.
HDD\
      Select this disk and set it up as /home under the mount point option and this will make all your users automatically store their personal files under this disk.
       As a more complex secondary option you can use Ubuntu's manual partitioning options to set split the HDD's disk space into a /home and separate partition as /media/storage or other name , as described in the previous example.

You also mentioned saving files from the web , and I'm guessing it's from a web browser. You can always set up you browser to always ask where to save files or you can set up a custom download folder ( and move the files afterwards to a more permanent location on the HDD).

Enjoy your Ubuntu! :)

---

### Post by G33shooter on 2015-05-05
Thank you for the great write up/help. I think I'll go with option 1.  That said, I already own a 1TB 7200 hdd, but not the SSD.  Will an SSD be much faster or will I not really notice the difference in speed?  If the difference is noticeable, is a 60GB SSD big enough for setup 1 that you mentioned, or would I be better off getting a 120 or 250GB SSD?  (I've never used an SSD before, I just figured since I'm starting this fresh build, why not.)

---

### Post by etescartz on 2015-05-05
Ubuntu and most of the software you'll probably install on this computer (unless you're planning on installing Steam games) will not take more than 60 GB of disk space, even after some time. I would recommend getting a larger SSD drive, if you are willing to spend the required amount of money because in the long term , you'll probably want to store more and more files on it. 

Probably not image/video/audio/game files, but you could always split it into 2 partitions and dualboot with other linux distributions or even "that other OS" :)

     If you're new to SSD drives in general and you have 30 minutes of spare time you could install same OS (in your case, Ubuntu) on both disks.
Ignore one of the disks completely , let's say you start by installing on SSD , and you don't select any mount options for the HDD.
Just use full disk install so you don't lose any time with setup options, then boot into it, do some quick update/upgrade..
   Maybe you could install a few programs.. 

   Then install Ubuntu again , but ignore the SSD this time ,and just do the same full disk installation on the HDD , and try using it for a few minutes like I described.

   Don't worry , as GRUB boot loader will pick up any other operating system already installed on any other drives and you'll be able to choose between them (if you don't feel confident enough that you'll be sure which one of the boot options is which , you could install a older or newer version of the Ubuntu flavor you want to use).

   After that you can reboot into each a couple of times and I'm sure you'll notice the difference in performance depending on the boot option you selected.

   SSD drives are great performance enhancers for computers.
   Another option to consider would be to buy a Seagate Hybrid drive or SSHD. You can read about it [here]("http://www.seagate.com/gb/en/solutions/solid-state-hybrid/") .
It's supposed to be the best of both worlds. This what I'll go for next time I'll be interested in purchasing a new disk drive.

---

### Post by G33shooter on 2015-05-05
Awesome. Got some more reading to do! I've never even heard of hybrid drives :) thanks again! I think I'll grab the 60 gb SSD since it's cheap and play around with that and the hdd setup. I can always upgrade to a larger SSD later if I feel like I need to (then just use the 60 gb SSD with enclosure as an external hard drive for my laptop.)  thanks for all the help!

---

### Post by AraiBob on 2015-05-06
Sir,

About 2 years ago, I did what you proposed. I put /home on the hard drive and all else under / on the ssd. Over time I realized this was 'partly' a waste of time. When I installed 14.04LTS, I put all on the sdd and only put directories for downloading onto the hard drive. I point applications used for downloading onto that set of directories on the hard drive. 

The SSD is using only 17GB of 251GB on the SSD (Samsung 240 Pro). The hard drive (1TB WD Velociraptor) is using 143 GB. This has been working for over a year for me, with no problems.

Good luck, AraiBob

---

### Post by tokyobadger on 2015-05-06
I'd suggest reading up on SSDs in general and then in linux before spending any cash:

1) [This buyers' guide from 2013 at Anandtech](http://www.anandtech.com/show/7545/best-ssds-holiday-2013) basically explains why you may regret a smaller sized SSD

2) [This Archwiki article on SSDs](https://wiki.archlinux.org/index.php/Solid_State_Drives) is also a valuable read on how to get the most out of your SSD under linux - note the sections on TRIM and related recommendations for /etc/fstab flags  

3) I would increase the RAM to 16G and skip a swap partition - [this Ubuntu FAQ](https://help.ubuntu.com/community/SwapFaq) on swap is a good read - swap is important for suspend-to-disk

4) if you do put swap on the SSD instead of adding more RAM don't apply the discard flag and consider lowering the swappiness value in/etc/sysctl.conf to reduce writes to the SSD [tutorial here](https://sites.google.com/site/easylinuxtipsproject/ssd) - some other good tips there too

Good luck with the build and the install

---

### Post by oldfred on 2015-05-06
My first SSD was 60GB I had two / (root) partitions, one my main working install and the other for testing or next install.
I also kept /home inside / but used a /mnt/data partition on hard drive and in effect moved all my data folders like Music, Documents etc into the data partition. Then  a default save in / really was into the data partition on the hard drive. 
I also left 25GB space on hard drive for another / so I could have an install on it in case SSD failed.

My new system has a larger SSD, but I have not figured out what to do with all the room. :)
I also suggest using gpt partitioning, if a newer system with UEFI or an older system but not planning on dual booting with Windows. Windows only boots with UEFI on gpt partitioned drives. Ubuntu does not care.

```
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name     Flags
 1      1049kB  525MB   524MB   fat32           efi      boot
 2      525MB   527MB   2097kB                           bios_grub
 3      527MB   26.7GB  26.2GB  ext4            trusty
 6      121GB   121GB   105MB   fat32                    msftdata
 5      121GB   126GB   5163MB  ext4            iso_ssd
 4      126GB   128GB   2000MB  linux-swap(v1)


Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  525MB   524MB   fat32           EFI System Partition  boot
 2      525MB   527MB   2097kB                                        bios_grub
 3      527MB   26.7GB  26.2GB  ext4            vivid
 4      26.7GB  446GB   419GB   ext4            data
 5      446GB   476GB   29.9GB  ext4            backup
 8      711GB   713GB   2000MB  linux-swap(v1)
 7      713GB   993GB   280GB   ext4            homerun
 6      993GB   1000GB  7337MB  ext4            iso_hdd


```

How I linked data partition is in these discussions, I used shared data as I boot several Ubuntu, but want same data in all of them, but also works well for SSD & HDD configuration:

 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by G33shooter on 2015-05-07
Thank you Arai, Tokyo, and Fred, for the info and great reads.  :smile:

---

