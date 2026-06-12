---
title: "installation on SSD HardDisk and paritions?"
date: 2015-09-09
forum: Installation &amp; Upgrades
---

### Post by greentea2 on 2015-09-09
Hi all, 

I've found this post on a Linux Mint forum and I would like to ask if I basically could apply the same for installing Ubuntu. In my case I only have a 120gb SSD.
 
Should I do a partition: home and root ? 
Would be 20gb enough for home in Ubuntu ?

[quote="Derek_S"]..... - Instead of linking you to a general tutorial that's vague or missing important information, here's one that applies to you and your specific situation. Basically, you have two choices. If you want to keep it simple, all you need are two disk partitions, one for root and one for swap. If you want to take it to the next level and isolate your data files from your operating system files, then you need three disk partitions: one for root, one for swap, and one for home.

1.) Swap - If you want to hibernate the system, then you will need to make swap equal in size to your system memory. For example, if you have 4GB of system memory, then swap should be 4096MB in size. 8GB of memory, then make swap 8192MB, etc.

If you are not concerned with using hibernation, then you should create a swap partition keeping this in mind: Systems with a lot of memory don't need a lot of swap. Systems with very little memory need more swap. Examples: If you have 8GB or more of system memory, and you don't want to use hibernation, you can make swap quite small, say 2GB. However, if your system has just 1GB or 2GB of memory, you should consider making swap 4GB in size, maybe even 6GB. I suggest doing some Google searches for yourself and see what other people recommend for swap.

2.) Root - If you're only creating swap and root, then create swap first and then use most of the remaining space for root ***(see NOTE below). If you're thinking about creating a third partition for home, create swap first, then create root and make it 20GB in size. Then use most of the remaining space for home ***(see NOTE below). You should format swap as linux-swap, and format both root and home as ext4.

***NOTE: You will find your 240GB SSD isn't actually 240GB. It's formatted capacity will be about 223.5GB. Also, you should leave roughly 10% of the space on it as unallocated space. This is so the SSD's firmware has a small amount of space available to perform functions such as wear leveling and garbage collection. So try to keep the total partitioned area on the disk at 200-205GB. Take this into account when planning your partition setup and do not extend the last partition to the very end of the disk.  

3.) If Linux Mint is the only operating system you're planning to install on your SSD, and you'll only have two or three partitions on the disk, then keep it simple. Go into your BIOS settings, and enable Legacy/CSM as the boot mode. Make sure UEFI boot mode and Secure Boot are both disabled.

4.) Boot your machine using your Linux Mint installation media, then make your internet connection. Go to Menu > Preferences > Gparted. Examine the lower panel and verify the 240GB SSD is displayed there. If not, use the tab on the right side to toggle between /dev/sda, /dev/sdb, etc. until it appears there. Once you are certain you have selected the correct device, go up and click "Device", then select "Create Partition Table". The default choice is "ms-dos", which is what you want to use since it is compatible with using Legacy/CSM boot. Now click "Apply", a new partition table will be created on the disk, and you will see a single line marked "unallocated" appear in the lower panel. Leave Gparted open, since the next step is creating your Linux partitions using Gparted.

5.) Now go to the lower panel and right-click the line marked "unallocated", then select "New". For each new partition you create, you must do four things: a.) Size: Enter the size in MB. Remember, MB = GB x 1024. b.) Align to: Select "MiB" for SSD device. c.) Create as: Select "Primary". d.) File system: Select "linux-swap" for swap and "ext4" for root and home. Optional: For Label: Enter Root, Swap, or Home to identify your new partitions. After doing this, click "Add", then go back, right click on "unallocated", and create the next partition.  

I suggest creating your Linux partitions in this order: swap, then root, then home. This way, if you ever decide to add another Linux OS in the future, you can use Gparted to shrink the last partition on the disk, create an extended partition for the new OS, then create logical partitions within the extended partition. It always pays to plan ahead. Also remember what I mentioned about partition sizes in steps #1 and #2 and about leaving some unallocated space as explained in ***Note.

6.) Once you have created all of your Linux disk partitions, and are satisfied with the results, then you can proceed by going up and clicking "Edit" and selecting "Apply All Operations". (Note: You also have the choice of undoing the last operation or cancelling all operations entirely if you need to change anything.) Doing this is what actually creates all of your new disk partitions. One more thing I like to do: Find the line for swap, then right-click it and select "swap on". This mounts and activates the swap partition prior to installation, which is helpful on systems with a small amount of installed memory. You are now finished and can close Gparted.        

7.) Now you can perform the installation, and when you get to the screen "Installation Options", use the "Something Else" option to install. On the next screen, for each new Linux partition, you must do three things by clicking the line where each one is displayed and then clicking the "Change" button: a.) For "Filesystem", use "ext4" for both root and home. If you did not turn "swap on" in Gparted, then use "linux swap" for swap. b.) For "Mount Point", use " / " for root, and "/home" for home. If you did not turn "swap on" in Gparted, use "/swap" for swap. c.) For root and home, check the box marked "Format". There's no need to do this for swap. After doing this for each Linux partition, click "OK".  

Once you have done this, there is one very important thing left. Go down to where you see "Device for bootloader installation", and select "dev/sda". DO NOT select anything that includes a number! Then click "Install" to proceed. 

8.) Never forget the password you create for root. You'll need it to log in as root, run most of the administrative apps, and to execute Terminal commands.

9.) After rebooting, performing the initial system update, and getting everything set up the way you want, here is a tutorial you should read explaining how to optimize Linux Mint for use on your SSD drive: [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)[/quote]


Thanks in advance for any help. ;)

---

### Post by Bucky Ball on 2015-09-09
/home and /swap are best on a regular HDD if you have one and reserve the SSD for operating systems. If you only have the SSD, then /, /swap and /home are fine. Thing to remember is that you should leave some headroom on the SSD. You would want 20Gb of free, unallocated space, for instance. The debate continues on that one, but some headroom is a good idea with SSDs (and a bit on a hard drive avoids problems also). 

Just posting a link rather than the whole post is fine. :D

2Gb is fine for /swap unless you're hibernating. You don't need more.

As for whether what works on Mint is going to work on Ubuntu, don't know. Never used it and it is not supported in the main support areas here. There is an area, though, specifically for Mint users, but we advise that it is better to post on Mint's active forums. Unsure why you're looking at Mint instructions when you are installing Ubuntu. See [here]("https://duckduckgo.com/?q=install+ubuntu+14.04"). If Ubuntu is the only OS you can install in EFI or legacy (depending on age of hardware and BIOS). As you don't have Windows on this blank drive it doesn't matter.

If you have Win already installed on another drive, though, it will probably be installed using EFI. Then you have to use EFI for the Ubuntu install.  

Good luck.

PS: When you say, 'Should I do a partition, home and root', I'm a bit confused. Do you mean two partitions? /home and /? Home and root are not one partition ... :-k ;)

---

### Post by oldfred on 2015-09-09
Generally it looks the same for Ubuntu.

I prefer now to use gpt partitioning. Whether UEFI or BIOS. And if system is newer UEFI there are some advantages to UEFI. Or if drive will possibly be moved to a newer UEFI system then using gpt and having both the ESP - efi system partition(UEFI) and a bios_grub(BIOS/CSM) partition does not use much space. I use 25GB for / but have all data in /mnt/data on HDD with folders linkded back into /home inside /. But then my SSD does not have much use, so I have space for another install or two.

```
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name     Flags
 1      1049kB  525MB   524MB   fat32           efi      boot
 2      525MB   527MB   2097kB                           bios_grub
 3      527MB   26.7GB  26.2GB  ext4            trusty
 6      26.7GB  53.0GB  26.2GB  ext4
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
 9      476GB   501GB   25.0GB  ext4            wily_b
10      501GB   527GB   26.2GB  ext4            trusty_3
 8      711GB   713GB   2000MB  linux-swap(v1)
 7      713GB   993GB   280GB   ext4            homerun
 6      993GB   1000GB  7337MB  ext4            iso_hdd

```

---

