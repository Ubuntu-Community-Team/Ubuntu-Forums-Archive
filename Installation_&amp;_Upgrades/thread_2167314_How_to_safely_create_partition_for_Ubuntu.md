---
title: "How to safely create partition for Ubuntu?"
date: 2013-08-13
forum: Installation &amp; Upgrades
---

### Post by peter1897 on 2013-08-13
I have Windows 7 installed on my laptop and i want to install Ubuntu 12.04 alongside. My hard rive is separated on three partitions:

C=25GB
D=80GB
E=42GB

Window 7 is installed on C partition. On E partition i have 12GB free space and i want to take 8GB from this free space and create new partition on which to install Ubuntu. 

My question is, what is the safest way to create this partition without losing any data on E drive?

---

### Post by Boab1993 on 2013-08-13
Hi peter1897,

The safest way is to backup or copy all data on E to say D/C drive or an external drive; and re-partition E to 4GB.

Move all data back onto E.

Partition the unallocated space using the ubuntu live CD and install.

Bob's your uncle.

---

### Post by fantab on 2013-08-13
> **peter1897 said:**
> I have Windows 7 installed on my laptop and i want to install Ubuntu 12.04 alongside. My hard rive is separated on three partitions:

C=25GB
D=80GB
E=42GB

Window 7 is installed on C partition. On E partition i have 12GB free space and i want to take 8GB from this free space and create new partition on which to install Ubuntu. 

My question is, what is the safest way to create this partition without losing any data on E drive?

Backup all important DATA on 'E'.
Follow the instructions **[HERE]("http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html")** to Shrink the E partition and leave yourself 10GB of free 'unallocated space'. Apply the changes and leave Windows. 
Boot with your Ubuntu DVD/USB and 'Try Ubuntu without Installing'. Let the desktop load. Open [Gparted]("http://www.dedoimedo.com/computers/gparted.html") and from the 'unallocated space' create:
9GB Primary Ext4 Mountpoint '/'
1GB Extended
1GB Logical SWAP

(We can only have FOUR Primary Partitions to make more partitions we use an Extended Partition, which is a Primary Partition and acts as a 'container' for LOGICAL Partitions. SWAP is not an ablsolute must but it is recommended that you have one at least of about 512MiB).

---

### Post by TheFu on 2013-08-13
MBR partitions only support 4 Primary partitions and 100+ logical partitions.

GPT partitioning supports 100+ primary partitions, but is only supported by newer OS ... Win7 and later, plus Linux from at least 2010 and later (maybe earlier versions).

There are lots of other reasons to use GPT partitions, but there isn't an easy migration path. The first 4 partitions on GPT are backwards compatible with MBR ... in theory. Plus GPT breaks the 2TB MBR HDD size limitation. Anyone running over 2TB HDDs is using GPT - almost certainly.

The question asked about the "safest way" .... so I won't bother suggesting:
* for each partition, defrag. Imn theory, this should move all the data towards the front of the partition - doesn't always work. I've had to delete Windows swap files - which cannot be moved.
* use gparted to resize to make room for Linux
* create the partition you want for Linux where you want it. Can be logical or primary.
* create a 1G partition for swap "somewhere". Can be logical or primary.

Bob's your uncle .... 90% likely.  10% of the time, stuff screws up and data loss happens.  Backup, backup, backup. Practice a restore, then get started with your re-partitioning.

---

### Post by peter1897 on 2013-08-13
This partitioning and partition labeling is little confusing under Linux. I hope i don't mess up something. 

By the way, do i have to install Ubuntu on primary partition? In windows Disk Management it shows that i have 3 primary partitions.

[[IMG]http://img547.imageshack.us/img547/6093/5b59.png[/IMG]]("http://img547.imageshack.us/i/5b59.png/")

---

### Post by TheFu on 2013-08-13
a) Don't use Windows to modify Linux partitions. NEVER. Use only gparted or parted.  Don't trust "fdisk" under any OS anymore. fdisk may or may not work properly with advanced format disks or GPT disks. It is easier for us to just use tools that always work - **parted** and **gparted**.
b) Linux can be installed in a logical partition. No reason NOT to do that.  Only old OSes need to be installed in a primary partition - things like the recovery OS or hardware tools for laptops.  I don't think Windows has cared in years - definitely not since Vista perhaps even XP.

---

### Post by peter1897 on 2013-08-13
> **TheFu said:**
> a) Don't use Windows to modify Linux partitions.

Then, is it ok to use windows to shrink my E drive and then use Gparted to partition the unallocated space?

---

### Post by Cheesemill on 2013-08-13
> **peter1897 said:**
> This partitioning and partition labeling is little confusing under Linux. I hope i don't mess up something. 

By the way, do i have to install Ubuntu on primary partition? In windows Disk Management it shows that i have 3 primary partitions.



Unfortunately because of the way your drive is partitioned you can't just simply take some space from E: and create a new partition to install Ubuntu.

You're only allowed 3 primary partitions and 1 extended partition which is what you already have. Any new logical partition that you want to create has to go ***inside*** the existing extended partition (in the green box on your screenshot).

It is technically possible to shift everything around using Windows and gparted but you'd have to do it like this...
[LIST]
[*]Shrink E: by 10GB
[*]Move E: all the way to the right
[*]Move C: all the way to the right
[*]Grow your extended partition to take up all the available free space.
[*]Create your Ubuntu / and swap partitions in the free space inside your extended partition
[/LIST]


I really wouldn't recommend this though as any partitioning operation carries an element of risk, especially one as complex as this. It will also take a ***very*** long time and it will probably break your Windows boot loader which will need repairing.

If you are going to try this make sure you have ***[COLOR="#FF0000"][SIZE=2]BACKED EVERYTHING UP FIRST[/SIZE][/COLOR]***.

Another thing is that you can just install Ubuntu on 10GB of free space but it will be very tight. By the time you've allocated 1GB for swap and installed you'll have pretty much no space left  for documents or installing applications and upgrades.

---

### Post by TheFu on 2013-08-13
@Cheesemill makes excellent points.

The easiest AND safest way to solve a number of your issues is to buy a new, larger, HDD and setup GPT (lots of reasons why), then mirror each current partition on the new HDD. You'll have lots of room at the end of the HDD for more stuff.

BTW, I've run Lubuntu in 10G for many years. Added 4G more just last fall and still have 2.5G free.   I keep large file somewhere else, not inside the Linux OS/App partition.  There are lots and lots of partitioning recommendation threads in these forums. I write about the same thing to a new thread here about once a month.

It looks like you have a 160G HDD currently. A 320G HDD should be $30-$40, so I'd call that a great investment. If this is a desktop, then a 1TB HDD is $60 or so.

---

### Post by peter1897 on 2013-08-13
I have another problem. When i try to shrink E drive it shows that it can shrink only 453 MB even so i have 11GB free space. How to proceed? Can i set the shrink size to 10GB if it shows 453MB available? 

[[IMG]http://img825.imageshack.us/img825/4391/icr5.png[/IMG]]("http://img825.imageshack.us/i/icr5.png/")

---

### Post by Cheesemill on 2013-08-13
You probably can't shrink it because it's too heavily fragmented or there is an unmoveable file in it.

Check the Application Log for 'Event 259' to get more information

You could try defragmenting it a few times.

---

### Post by TheFu on 2013-08-13
> **Cheesemill said:**
> You probably can't shrink it because it's too heavily fragmented or there is an unmoveable file in it.

Check the Application Log for 'Event 259' to get more information

You could try defragmenting it a few times.

I had the same issue. Had to delete the Windows swap file, defrag, then resize.
Windows seems to like putting "unmovable" files at the far end for some reason. Boo on that.
[http://blog.jdpfu.com/2010/08/19/windows7-disk-shrinking-drama](http://blog.jdpfu.com/2010/08/19/windows7-disk-shrinking-drama) explains what I did.

---

### Post by peter1897 on 2013-08-14
I did defragmenting of E drive and now it shows that i have 11333mb available to shrink.

Something else i want to ask: If during the Ubuntu installation i mess up the master boot record and my laptop can't boot neither to window 7 or Ununtu what can i do then?

---

### Post by TheFu on 2013-08-14
> **peter1897 said:**
> I did defragmenting of E drive and now it shows that i have 11333mb available to shrink.

Something else i want to ask: If during the Ubuntu installation i mess up the master boot record and my laptop can't boot neither to window 7 or Ununtu what can i do then?

Run boot repair [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) from a liveCD of Ubuntu. Might need to install it, but that works from the liveCD too.

---

### Post by peter1897 on 2013-08-14
What file system to use ext3 or ext4?

---

### Post by TheFu on 2013-08-14
> **peter1897 said:**
> What file system to use ext3 or ext4?

If you don't know, then **ext4** is probably the answer you need.  There are 10 other Linux file systems too - each with strengths and weaknesses for any specific purpose.

I use EXT2, EXT4, JFS, XFS, and ZFS for different needs.  I hope to use BTRFS someday, but I don't think it is stable enough to risk any data yet.  EXT4 wasn't used here until last year - it was too new to risk our data.  I've been using JFS since the mid-1990s and never lost any data using it.  I am slowly moving the JFS stuff to EXT4 now. It is a great general purpose file system.

I use EXT2 inside VMs and for /boot mounts. Lower overhead and journaling happens outside the VM, so why have it inside too?

As you can see, lots of choices, but when in doubt, ext4 is probably the best overall choice today.

---

### Post by peter1897 on 2013-08-14
I have question about Ubuntu bootloader: After installing Ubuntu it installs its own bootloader which replaces the original bootloader that Windows 7 has. And when i want to boot Windows 7 the Ubuntu bootloader is booting it. 

Is that correct?

---

### Post by peter1897 on 2013-08-14
I am trying to create a new partition from my new unallocated space using GParted but when i select "New" it says that i can't create more than 4 primary partitions even so i want to create extended partition, not primary.  Why it doesn't let me create extended partition, only primary?

---

### Post by TheFu on 2013-08-14
An "extended partition" **is** a form of "primary partition."  You have used the 4 already.
Didn't I recommend GPT over MBR for partitioning? This is one of the many reasons why. GPT can have hundreds of primary partitions.

---

### Post by peter1897 on 2013-08-14
This partitioning thing is confusing for me. I never play with MBR before and i have used only Windows so far.
Can you tell me how to switch from MBR to GPT? Is that too complicated?

---

### Post by oldfred on 2013-08-14
You cannot switch a Windows drive to gpt unless you reinstall and have UEFI not BIOS. Windows only boots from gpt drives with UEFI. I have dual booted with XP on a MBR drive and Linux on a gpt drive.

You have to convert one of your existing "drives" or really partitions to the Extended partition. It will erase all data as the extended partition is just a container for the logical partitions. So back up data and erase one partition. 
Then inside the extended partition you can create many logical. 

You only can have one extended partition. And your first post shows D: as a logical partition, so you may have to move partitions around so you can increase the size of the extended partition that d: is inside. After any change to the size of a NTFS partition, boot Windows and run chkdsk before doing anything else.

---

### Post by TheFu on 2013-08-14
> **peter1897 said:**
> This partitioning thing is confusing for me. I never play with MBR before and i have used only Windows so far.
Can you tell me how to switch from MBR to GPT? Is that too complicated?

Sure.
1) completely backup all data on the entire drive 100%. Everything on the drive will be wiped.
2) Tell either Windows or Gparted that you want GPT partitioning in their tools.
3) Create partitions using **Windows** (vista or later) or **gparted** or **parted**.  **DO NOT USE [FONT=Arial Black][COLOR="#FF0000"]fdisk[/COLOR][/FONT] ever again.** In the future, fdisk may work properly with GPT and "Advanced format HDDs", but for now, it doesn't.  Close relatives to fdisk shouldn't be used either - cfdisk, sfdisk ... don't use those anymore.
4) Load your data and/or OSes back on the HDDs.

Profit!

There are caveats.  Old OSes ... like Windows-recovery partitions and PC vendor HW utility partitions need to be in the 1st 4 primary partitions of the GPT disk.  OSes older than Vista (around 2008) do not understand GPT, so those will not be bootable on this drive unless they are in the 1st 4 partitions. There may be cylinder limits for those older OSes too.  MS-Vista and current Linux systems can be booted fine from GPT partitions.  I like to have 2-3 extra 14G partitions just for different Linux OS testing. Heck, on a 1TB HDD, why not?  If you want more information - read the wikipedia article on GPT.

Do not skip step 1.  All your existing data on that HDD will be gone.

Afterthought:
If you create the GPT HDD using Windows tools, it will reserve a partition for something and you can boot Vista, Win7 off that drive.  I was under the impression that the new 900G HDD was empty and available for Linux use/booting.  I didn't think you were planning to move the Windows install off the other HDD. If you are, then you probably want to consult with more experts.

---

### Post by peter1897 on 2013-08-14
I can try this when i buy one external hard disk because now i don't have where to backup the data from my whole disk. 

I think i will try to change E drive from primary to logical using Easeus Partition Master to reduce the number of primary partitions.

---

### Post by oldfred on 2013-08-14
You cannot directly do that.

You already have the one allowed extended partition and it is not adjacent to your e: partition. If it was adjacent you could probably convert it to logical so both partitions are inside the one existing extended. 

All logical partitions must be in one extended partition and you cannot have a primary in the middle.

---

### Post by peter1897 on 2013-08-15
Can i move the unallocated space to the extended partition and create one logical partition for Ubuntu install and one logical partition for the swap file? 

[[IMG]http://img825.imageshack.us/img825/6642/gf83.png[/IMG]]("http://img825.imageshack.us/i/gf83.png/")

---

### Post by TheFu on 2013-08-15
The graph above shows where on the disk each partition is, relative to the other partitions.  Partitions must be contiguous.  To make the extended partition larger, you'll want to resize the partitions to the right of it smaller, then shift the the far right partition farther to the right, followed by shifting the next far right partition as far as possible to the right.

After that, THEN you can make the extended partition larger and put more partitions inside it or make existing partitions inside larger or some mix of that.

Clear as mud?

---

### Post by peter1897 on 2013-08-15
I thought i just can drag the unallocated space to the extended partition. I guess not.

I think i have to backup the whole drive and reformat it completely. I have to postpone Ubuntu install because i need to buy external disk for the backup files.

One question: Does logical partitions can exist only inside extended partitions?

---

### Post by TheFu on 2013-08-15
> **peter1897 said:**
> I thought i just can drag the unallocated space to the extended partition. I guess not.

I think i have to backup the whole drive and reformat it completely. I have to postpone Ubuntu install because i need to buy external disk for the backup files.

One question: Does logical partitions can exist only inside extended partitions?

Yep. Extended partitions and logical partitions are a kludge.  There is a great wikipedia article about MBR partitioning. It explains lots of stuff.

GPT is meant to solve all the current MBR kludges that we've been living with since the early 1980s. In 20 more years, we'll be complaining about GPT kludges ... perhaps. ;)

---

### Post by peter1897 on 2013-08-15
If i want to install Windows 7, Windows XP and Ubuntu what is the best way to partition the hard disk?

---

### Post by oldfred on 2013-08-15
You want each Windows in its own primary partition. And if you want to directly boot each from grub.

 To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by peter1897 on 2013-08-16
From the screenshot i posted above it seems like my outer partition is Toshiba System Volume, which is put there by Toshiba, my laptop is Toshiba Satellite A205 by the way. I am not sure if i need it, i think it is there to restore the factory settings. 
I have read that the outer partition are transferring the data faster so i want to put the partitions for the operating systems i want to install in the beginning of the disk, first partition for Windows 7, second for Ubuntu and third for Windows XP.
My question is can i delete this Toshiba System Volume partition?

My other question is if i will use Grup do i have to create partition for it which will be the first partition on the disk before any others?

My third question is why GParted doesn't show the MBR sector? Is it hidden?

---

### Post by oldfred on 2013-08-16
MBR is not a partition, just the  very first sector of the hard drive. Every partition also has a PBR or partition boot sector which is just first sector of a partition. Windows has essential boot info in every NTFS PBR.

You  need to make a set of recovery disks if you are thinking of removing Toshiba recovery partition. It should allow you to do that but will be several DVDs. 
There is no real advantage to one place on drive vs. another. 

You do not need a partition for grub as it is in several places on a drive. It is in MBR, in /boot and some configuration files are in Ubuntu.

---

### Post by peter1897 on 2013-08-16
I guess it is not possible to replace Windows 7 bootloader with Grub without installing Ubuntu. Correct?


Also, can i create more than one extended partition?

---

### Post by oldfred on 2013-08-16
Not really for a beginner as you install grub and have to always manually configure as Ubuntu has the scripts to do auto configuration. 

Theoretically you could install grub2 to the NTFS partition, but have to make sure grub's /boot folder is the same as the /Boot/BCD folder. In Windows case does not matter but /Boot and /boot then would be duplicate entries and not allowed. Also you have to manually create a chain load entry to chain load to the Windows PBR or partition boot sector which tells Windows to load bootmgr using BCD.

---

### Post by TheFu on 2013-08-16
> **oldfred said:**
> Not really for a beginner as you install grub and have to always manually configure as Ubuntu has the scripts to do auto configuration. 

Theoretically you could install grub2 to the NTFS partition, but have to make sure grub's /boot folder is the same as the /Boot/BCD folder. In Windows case does not matter but /Boot and /boot then would be duplicate entries and not allowed. Also you have to manually create a chain load entry to chain load to the Windows PBR or partition boot sector which tells Windows to load bootmgr using BCD.

Are we sure that Win8 wouldn't see an alternate, non-approved, boot loader as a virus or hack attempt and refuse to run?

---

### Post by oldfred on 2013-08-16
I do not know how to install grub only in UEFI mode. I expect there is a way, but do not see a reason for it. The efi folder works like multiple MBR in that every system has its own folder in the efi partition to use for booting. One advantage of UEFI over BIOS.

Grub has shim which is the secure boot with Microsoft signed keys. So grub in UEFI still works with secure boot on.  And with secure boot off any UEFI system should boot. But some vendors have modified UEFI to only boot efi files in efi partition with certain names.

 Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

### Post by peter1897 on 2013-08-17
I deleted my first partition which was Toshiba System Volume primary partition so i was able to create on more primary partition with ext4 file system. But it doesn't allow my to create another partition for the swap file. 
Can i install Ubuntu on the new partition and than create the swap partition? I guess after installing Ubuntu it will install Grup and i would be able to create more than 4 primary partitions. Correct? 

[[IMG]http://img809.imageshack.us/img809/8898/u24d.png[/IMG]]("http://img809.imageshack.us/i/u24d.png/")

---

### Post by Cheesemill on 2013-08-17
> **peter1897 said:**
> I deleted my first partition which was Toshiba System Volume primary partition so i was able to create on more primary partition with ext4 file system. But it doesn't allow my to create another partition for the swap file. 
Can i install Ubuntu on the new partition and than create the swap partition? I guess after installing Ubuntu it will install Grup and i would be able to create more than 4 primary partitions. Correct?

No.

The 4 partition limit has nothing to to with grub or any other bootloader.

The only way you can shift your partitions around to be able to create more partitions is by creating unallocated space inside your extended partition, just as I outlined in [post #8]("http://ubuntuforums.org/showthread.php?t=2167314&p=12755382&viewfull=1#post12755382").

---

### Post by peter1897 on 2013-08-17
I thought the swap file is recommended but not mandatory, and i thought i can install Ubuntu first and then create the swap file.

Then can i move the unallocated space from the first partition to the extended partition and create one logical partition for the swap file?

I made a mistake between Grub and GPT, so i thought Grub support more than 4 primary partitions. But i guess i still need to install Grub because Windows MBR doesn't recognize linux.

---

### Post by TheFu on 2013-08-17
> **peter1897 said:**
> I thought the swap file is recommended but not mandatory, and i thought i can install Ubuntu first and then create the swap file.

Then can i move the unallocated space from the first partition to the extended partition and create one logical partition for the swap file?

I made a mistake between Grub and GPT, so i thought Grub support more than 4 primary partitions. But i guess i still need to install Grub because Windows MBR doesn't recognize linux.

Swap files are not mandatory, but only experts should work without one and only on systems with very well-know workloads. Without a swap file, really bad things are likely to happen without any warning, especially on a desktop machine.  You really, really want a swap partition. The generally accepted size is 2G or however much RAM is inside the box - whichever is larger.  Swap files are different from swap partitions. There are positives and negatives for each - partition or file. The swap partition pros overwhelm the swap file option completely, which is why it is the default for Linux systems.

Seems we got you all confused.  MBR is about partitioning - it is platform independent, not specific to Windows or Linux or ... whatever OS ...  The same is for GPT - platform independent.  The OS doesn't matter, though each OS may have limitations with each partitioning scheme and may not understand the other OSes inside other partitions.  MBR can only have 4 primary partitions - PERIOD. 1 of those can be an "extended partition."  The space for every partition must be contiguous.   Please read these to get the basic knowledge:
* MBR - [https://en.wikipedia.org/wiki/Master_boot_record](https://en.wikipedia.org/wiki/Master_boot_record)
* GPT - [https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table)
* Boot loaders - [https://en.wikipedia.org/wiki/Bootloader#Modern_boot_loaders](https://en.wikipedia.org/wiki/Bootloader#Modern_boot_loaders)
Grub is a boot loader. There are others, but grub is the most popular, most feature rich, for Linux on HDDs.

We've tried to outline the best solution for your needs since this thread started. There are many considerations that took years of experience to learn that went into the recommendations.

After you have a great backup of the HDD, try some different things that we've recommended. After all, you have a great backup, right? Failure doesn't mean anything bad and you'll learn a ton that way that discussing will never teach.  Backup first, then try things.

---

### Post by peter1897 on 2013-08-17
I shrink my logical partition in D and from the unallocated space i created two logical partitions, one for the Ubuntu install and one swap:

dev/sda6 - Ubuntu install
dev/sda7 - SWAP

I started the installation but when i get to the point when i have to choose devices for the install i have some doubts:

First, do i have to check dev/sda6 for the install or i have to check also the SWAP partition?
And second, what device to choose for the bootloader install - dev/sda or dev/sda6?

[[IMG]http://img11.imageshack.us/img11/4779/wmbw.png[/IMG]]("http://img11.imageshack.us/i/wmbw.png/")

---

### Post by oldfred on 2013-08-17
If sda6 is your ext4 partition, you choose it as / (root), you can check ext4 & format again. If swap exists it will find and use it. If you had the separate /home with your data, you would select it but not format it.

You have to install boot loader to sda.
BIOS only boots from the MBR of sda. Only if you had another boot loader in sda that would multi-boot could you possibly not install to sda. I do not like that it still shows the NTFS partition as a choice. We have filed bug reports on that for years as any grub install to a NTFS partition breaks Windows as it already has the Windows loader in it.

---

### Post by peter1897 on 2013-08-17
I installed Ubuntu and so far everything looks OK. I was able to boot Ubuntu and Windows 7 without problem.

How can i set Windows 7 to be the default OS to load on start up, because now the default is Ubuntu?

---

### Post by oldfred on 2013-08-17
Most new users just use Grub Customizer. I have never used it and just manually edit grub's files.

 Configuring the Boot Menu in Ubuntu - Boot Order in grub
[http://www.psychocats.net/ubuntu/bootmenu](http://www.psychocats.net/ubuntu/bootmenu)



 New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)
The Grub 2 Guide - drs305 also link to grub customizer
Ubuntu Community Documentation site
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by peter1897 on 2013-08-18
I have now Windows 7 and Ubuntu installed and i want to install also Windows XP. On dev/sda6 i have installed Ubuntu and on dev/sda1 Windows 7. On the last partition dev/sda4 i want to install Windows XP. 
How to proceed? Do i have to install Windows xp in the standard way? I guess it will overwrite Grub during the installation. How to repair it after this or can i backup Grub and restore it after the install?


[[IMG]http://img163.imageshack.us/img163/5652/t2df.png[/IMG]]("http://img163.imageshack.us/i/t2df.png/")

---

### Post by TheFu on 2013-08-18
I have never tried what you are attempting, but I was under the impression that the "best practice" was to load the oldest Windows OS first, then the next oldest, then the most recent .... only then, load any Linux or other alternate OS.  This is because WinXP doesn't know anything about Win7 and will screw with the booting.

I'm probably wrong.  If you are happy with what you have - make a new backup of everything and try it.  My version of Win7 supports running WinXP inside a VM, so does Ubuntu.  If you **need** WinXP to run old games, then I can understand going through this effect to have a real install. If you just need it to run some programs ... not high graphics ... then I'd use a virtual machine - provided your CPU and RAM is a core 2 Duo or better.

---

### Post by peter1897 on 2013-08-18
I have read that Windows XP should be installed on one of the first 4 partitions and i am planning to install it on my last partition. I will see if this will cause problem.

But i am still not sure what is the best way to repair Grub after the installation because Windows XP will overwrite it for sure.

---

### Post by TheFu on 2013-08-18
Don't know "best way", but the way that I'd do it is with "boot-repair".
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by peter1897 on 2013-08-18
I installed Windows XP and everything seems to working fine but something strange happened during the installation. This is what i did:

I first use GParted to hide the partition with my Windows 7 install and then i installed Windows XP. After the installation i loaded Ubuntu live cd and used Boot Repair to repair Grub. After restart i could see Windows XP in Grub menu and i was able to boot it without problem. But during the installation i think windows put the boot files in the adjacent dev/sda3 partition. This is a screenshot right after the installation of Windows XP.

[[IMG]http://img401.imageshack.us/img401/2427/8q2b.png[/IMG]]("http://img401.imageshack.us/i/8q2b.png/")

Windows XP is installed on dev/sda4 and boot files are on dev/sda3. These are the files on dev/sda3:

[[IMG]http://img22.imageshack.us/img22/8482/u45v.png[/IMG]]("http://img22.imageshack.us/i/u45v.png/")

Can someone tell me why windows installed the boot files on different partition? I even thought Windows can't boot if the boot files are not on the same partition as the Windows install.

What i have to do? Do i have to move these files to the Windows XP install partition?

---

### Post by oldfred on 2013-08-18
Windows MBR boots by looking for the active partition to boot from. We see that as the boot flag. Then in PBR - partition boot sector of active partition. it will have info to boot with ntldr for XP or bootmgr for Vista/7/8 in BIOS mode. But only one partition can have boot flag so with multiple installs of Windows all boot files are just in that one active partition.

Better explanation with pictures.
 To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by peter1897 on 2013-08-18
> **oldfred said:**
> 
 To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it.


What do you mean by install second product in it? I have to create one primary ntfs partition and install the two windows loaders there?  Or i have to set boot flag on on the two partitions, with Windows 7 and Windows XP? 

Drive E where Windows boot files are now is a primary partition and the only one without operating system installed on it. On the other two are installed Windows 7 and Windows XP. I can't create more primary partitions. 
I am using drive E for data storage so i guess the boot files should co-exist with the other files and folders. Would be that a problem? I will leave it like this if it will not cause a problem since the three operating systems are booting and functioning ok.

---

### Post by oldfred on 2013-08-18
Did  you read the link on how Windows works.

You should be able to repair each install to get its boot loader into its own install as long as both installs are primary partitions. You may copy boot files, & boot flag to second install and then using that installs repairs fix it if it does not work.

       Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by peter1897 on 2013-08-19
Under Windows XP i don't see the boot files. They are not in the root directory in any of the primary partitions.
Under Windows 7 i can see boot.ini on drive E but ntldr and NTDETECT.COM are not on any partition.
And why these two files AUTOEXEC.BAT and CONFIG.SYS are one E drive and not on Windows XP partition? They are not boot files. 

By the way, boot flag can be assign on only on partition, correct? Because if i assign the boot flag to Windows XP partition it removes the boot flag from Windows 7 partition.

---

### Post by oldfred on 2013-08-19
Yes Windows can only boot from one active partition, so each drive can only have one boot flag.

Boot.ini is a text file with info on which partition to boot from. An XP repair updates it but you can also manually edit it.  But you need ntdetect.com and ntldr in the XP partition.  You can use your XP install disk and use it to repair the XP install, but make sure you have boot flag on XP partition.

If you use your Windows 7 repair make sure you have boot flag on Windows 7 install. You can do some configuration of XP from a Windows 7 repair console.

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

   If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

   Boot files may need attributes also from Windows repair console:
attrib +r c:\filename
attrib +h c:\filename
attrib +s c:\filename

---

### Post by peter1897 on 2013-08-19
This is what contains the boot.ini file:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

If ntldr and NTDETECT.COM are not present Windows XP is booted by Grub, correct?    

I think to leave the things like this because if i have to reinstall Windows XP i have to repeat the whole process of setting up its own boot loader again.

---

### Post by oldfred on 2013-08-19
Grub cannot boot a Windows that does not have boot files. Those with multiple installs of Windows normally only have one Windows to boot from grub and then Windows boot.ini if 2 XP installs or BCD with later versions will show a boot menu for all Windows installs. See Post #50.

You do not have to reinstall Windows but do have to run separate repairs if you want to directly boot from grub menu.

---

### Post by peter1897 on 2013-08-20
Is it possible to make Windows 7 use linux swap partition instead of swap file and will using swap partition instead of swap file improve the performance of Windows 7?

---

### Post by Cheesemill on 2013-08-20
No, it's not possible.

---

### Post by peter1897 on 2013-08-20
If i install Windows 7 x64 and i have also installed Ubuntu x32 and Windows XP x32 what version of Boot Repair to use to repair Grub - x32 or x64?

---

### Post by oldfred on 2013-08-20
Boot-Repair is primarily for Ubuntu so I would use 32 bit. 

Just about all it repairs for Windows is the MBR which for Windows is the same for 32 & 64 bit. But your Windows rpairCD must match.

---

### Post by peter1897 on 2013-08-20
I reinstalled Windows 7 then i run Boot Repair but Windows XP disappeared from the Grub menu. It appears as "previous version of windows" when i first select Windows 7 from the menu but if i select the entry it can't boot. I can boot only Windows 7 and Ubuntu.
During the installation it removed also the E letter from drive E so i had to select another letter to make the drive visible in windows explorer. I don't why but E wasn't available for selection even so it is not assigned to any drive which is not good because it messing up the settings of my portable applications on that drive. 

I will try to fix the boot files from the repair console but if it doesn't work i will reinstall Windows xp.

---

### Post by peter1897 on 2013-08-21
I copy ntldr and ntdetect.com to Windows XP partition but it still can't boot. If i try to boot it shows  that ntldr is missing.

How to fix this? Why it is not finding the ntldr file when it is there?

---

### Post by oldfred on 2013-08-21
Try moving boot flag to the XP install and use the XP repair console to repair it. See post #54.

---

### Post by peter1897 on 2013-08-21
I reinstalled Windows XP because the Repair Console was missing in my install copy of Windows xp so i couldn't use it. After the install the three files boot.ini, ntldr and ntdetect.com was placed in C drive where is my Windows 7 installation but i still couldn't boot, it still showed that ntldr is missing.
Then i copy the three files to drive F with my windows xp install and used EasyBCD to set drive F as boot drive for Windows XP entry, because for some reason it had drive E set as a boot drive.

Now Windows XP is booting but how to add it to Grub menu? Before reinstalling Windows 7, Windows xp was showing in grub menu, now i have to select Windows 7 entry and then choose between Windows 7 and Earlier version of windows

---

### Post by oldfred on 2013-08-21
When you reinstalled XP did you move boot flag to the XP partition. It then should not have installed the XP boot files to the Windows 7 partition. You must have had boot flag on the Windows 7 partition.

Did you follow the instructions in the link in post #50 on dual booting two Windows so both appear in grub.

Have you run this in Ubuntu?
sudo update-grub

---

### Post by peter1897 on 2013-08-21
I didn't put the boot flag on XP partition because i thought that during the installation it is losing its boot status. I mean to install Windows XP on that partition i delete the partition and it becomes unallocated space and then formating it. When it become unallocated space isn't that make it lose its boot status?

I run sudo update-grub and now window xp is showing in grub menu and it boots directly when i select it. But when i select windows 7 entry it still shows two entry - Windows 7 and Earlier version of window. How to make it boot directly to Windows 7?

---

### Post by oldfred on 2013-08-21
That is a Windows question, but I think you have to remove the extra entry from the BCD. You can use bcdEdit in Windows.

[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

---

### Post by peter1897 on 2013-08-22
I used EasyBCD and fixed it. Not it boots directly to Windows 7 from Grub menu.

---

