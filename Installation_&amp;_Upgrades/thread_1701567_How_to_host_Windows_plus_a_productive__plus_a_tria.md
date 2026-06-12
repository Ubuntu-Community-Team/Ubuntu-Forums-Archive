---
title: "How to host Windows plus a productive  plus a trial Linux version on one PC"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by jolexin on 2011-03-06
I have been running a dual boot system with **Windows XP** plus **SUSE Linux 11.2** since january 2010. Now (2011-03-06) I downloaded **Ubuntu 10,4 LTS**, produced an installation CD, booted Windows XP and invoked the Wubi to instal Ubuntu under Windows. The good news is that it works! However, I would prefer a different setup. 

Currently, when my PC boots, I can choose from the GRUB menu either SUSE Linux or Windows. When I select Windows, I see another menu where I can choose between Windows and my new Ubuntu Linux. 

**I would like to install Ubuntu Linux such that my initial GRUB menu offers the choice between the three systems**. From a few articles in the Ubuntu forums I conclude that it should be possible to do so. 

**Is there an instruction on how to do it?**

I chose a headline that expresses my question in more general terms, which hopefully describes the need of many users.

---

### Post by oldfred on 2011-03-06
Welcome to the forums.

Is this all one one hard drive or do you have multiple drives? 

Grub2 is very good at automatically finding other systems and setting up a boot stanza to boot that system. Not 100% sure about Suse, but many systems have been found. If not, and a alternative is to install Suse's grub bootloader to a Suse boot partition and chainload. I used chainloading with old grub as that gave me a menu with the updated kernel to boot. Ubuntu's grub2 would require a sudo update-grub to find the new kernel with each update of Suse.

---

### Post by jolexin on 2011-03-08
My PC has got only one hard drive with the following partitions: 

# parted --list
Model: ATA HITACHI HTS54502 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

[FONT=Courier New][SIZE=2]Number  Start   End     Size    Type      File system     Flags            My Annotation 
------------------------------------------------------------------------------------------------------------------
 1 1049kB  92,7GB  92,7 GB  primary   ntfs            type=07        my Windows XP partition /windows/C
 
3      242GB   250GB   7702 MB  primary   fat32           type=12        Lenovo Diagnosis partition
 
2      92,7GB  242GB   150  GB  extended                  boot, lba, type=0f    The rest of my disk


 5      92,7GB  126GB   33,6 GB  logical   fat32           type=0b        my ALLDAT partition /windows/D[/SIZE][/FONT] [FONT=Courier New][SIZE=2]
 
6      126GB   160GB   33,6 GB  logical   fat32           type=0b        my BIFI partition /windows/E
 
7      160GB   193GB   33,6 GB  logical   fat32           type=0b        my DATSI partition /windows/F

 
8      193GB   195GB   2155 MB  logical   linux-swap(v1)  type=82        SUSE Linux swap partition[/SIZE][/FONT] [FONT=Courier New][SIZE=2]
 
9      195GB   214GB   18,9 GB  logical   ext4            type=83        SUSE Linux root partition

10      214GB   242GB   28,0 GB  logical   ext3            type=83        SUSE Linux home partition[/SIZE][/FONT][SIZE=2]
------------------------------------------------------------------------------------------------------------------[/SIZE]

I am thinking of using sda7 - my DATSI partition - as the root partition for Ubuntu Linux. 
I hope to use the swap partiton sda8 both for SUSE and Ubuntu Linux. Is that possible?
I wonder if I can reuse the home partition sda10 for Ubuntu Linux, provided that I create the same 2 users there?

Currently my Ubuntu Linux trial version resides inside my windows partition. 
Do I conclude correctly from your answer that I might proceed as follows:
(A) deinstall Ubuntu
(B) Boot from the Ubuntu CD, which will give me the choice to install Ubuntu
(B1) as part of the installation specify sda8 as swap partition, sda7 as root partition and (?) sda10 as home partition.

The result of the above process should then be the desired choice of 3 systems under the (Ubuntu?) GRUB bootloader?

---

### Post by snowpine on 2011-03-08
Your plan sounds (mostly) good. The reason you currently don't see all 3 options at once is because you're using Wubi. If you go with a "full" install of Ubuntu, GRUB2 should detect all 3 operating systems and give you the proper options at boot.

Yes, you can share the same swap partition between Ubuntu and SUSE.

Yes, you can share the same home partition too, BUT make sure you use different usernames for each distro! Personally my approach to this situation is to NOT use a separate /home partition for any of the distros in a multi-boot, but rather a separate partition that holds data and documents to share between the different OS's. If you use a Windows filesystem then you can share with Windows, too. :)

---

### Post by jolexin on 2011-03-09
Thank you! Your answer sounds encouraging. I will follow your advice with the separate data partition that I can share among different OS's.

---

