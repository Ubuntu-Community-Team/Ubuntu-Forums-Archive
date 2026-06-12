---
title: "Consequences after Resize/Move with GParted"
date: 2014-12-04
forum: Installation &amp; Upgrades
---

### Post by jack117 on 2014-12-04
Hi

I have a 500 GB HDD (C:155GB; D:155GB; E:155GB) and I installed Windows 7 in C drive.

Later my E drive was empty, so I deleted that partition and allocated it for Ubuntu 14.04 LTS **ext4** **(57.22 GB)**  **swap** **(98.03 GB)**

Now I want to resize (reduce the size) of my **ext4** drive and **swap** drive (to use the rest as an E drive in Win 7) as show in the attached pic's, I have resized them, **ext4 (39.6 GB)** and **swap (2.94 GB)** and got **unallocated 112.71 GB**. _I want to use this 112.71 GB as an E drive in Win 7. Is it possible???_

Although I haven't performed the operation to resize them cuz I got some warning msg's as I moved ext4.

after performing the operation will my system reboot??? resizing swap is not a problem but ext4 (that contains boot files) will effect my reboot?

[COLOR=#000000]I attached the pics in the order[/COLOR]

---

### Post by MAFoElffen on 2014-12-04
So the boot loader is Grub2? How much RAM memory?


I agree that 90-some GB's of swap was wasteful. Rule of thumg is 1.5 times your installed RAM for swap.

No, adding the unallocated as NTFS should not affect your installed boot to Linux, as Grub2 is setup using UUID numbers to point to the filesystem of a physical partition, not to the logical order of the partition as was with previous versions of Grub and Lilo.

Curious though-- I don't resize Windows partitions with GParted. It will do it... but it breaks the Windows index file. So when it boots the first time, it will have to rebuiild/repair that file. It is usually just an inconvenience, but sometimes that causes unexpected problems on older disks. I do used GParted, but just safer to do Windows partitions from inside Windows, and others with GParted.

---

### Post by fantab on 2014-12-04
[QUOTE=MAFoElffen]I don't resize Windows partitions with GParted. It will do it... but it  breaks the Windows index file. So when it boots the first time, it will  have to rebuiild/repair that file. It is usually just an inconvenience,  but sometimes that causes unexpected problems on older disks[/QUOTE]
Yes, it is a very good idea to use Windows partition tools to create a new windows partition... Windows Disk Management does the job.

---

### Post by jack117 on 2014-12-05
> **MAFoElffen said:**
> So the boot loader is Grub2? How much RAM memory?.

**Yes Boot loader is obviously, GRUB 2. It is only a 1.5 GB RAM, so if its 1.5 times then I should give it only 2.25 GB. what is purpose of swap?? **

> **MAFoElffen said:**
>  I don't resize Windows partitions with GParted

Glad you raised this point, I already did that before, I resized **swap** drive with **GParted** to **8 GB** and got **90 GB Unallocated** that appeared in **Disk Management** in **Win 7** but that **unallocated** is placed **after swap drive (means after 8 GB )** and when I right clicked and followed the steps to create New Volume in NTFS at the end it gave a msg that my system will reboot from the new volume created something like that (I don't remember it exact) 

I have attached Disk Management pics.  _[COLOR=#2f4f4f]How can I create partition from Win 7 by shrinking Ubuntu drives?[/COLOR]_

---

### Post by MAFoElffen on 2014-12-05
It's like the Windows Virtual Memory Paging file. People assume is is just for overflow of system memory that swaps into a memory page... but it is also for hibernation and sleep. When it goes into those 2 states, it wrtites the memory to disk in this in the swap space.

---

### Post by jack117 on 2014-12-05
Thank you 

what about the second half of the question

I will create partition with Win 7 only, but before that I have to free the volume from Ubuntu drives (I do that with GParted), so that I can create New Volume in Win 7 with Disk management (by right clicking on the unallocated volume that appear after D drive).

To do that I need **unallocated** space after D: drive right? I cannot have it at the end of swap drive! (at the far end)

[U][COLOR=#2f4f4f][COLOR=#000000]How can I create partition from Win 7 by shrinking Ubuntu drives directly with out GParted?[/COLOR]

[COLOR=#000000]If its not [/COLOR]understandable,[COLOR=#000000] I will give the screen shots [/COLOR][/COLOR][/U]

---

### Post by Mark Phelps on 2014-12-05
> How can I create partition from Win 7 by shrinking Ubuntu drives?

Well, first of all, let's get the terminology straight to prevent confusion.  Those are Partitions not Drives.  MS still calls them Drives, even though they are not.  A drive is a physical disk.  A partition is a space on the disk that is allocated, and usually then assigned a filesystem.  You are manipulating partititions, not drives.

Second, Windows does not understand Linux partitions, even if you could resize a Linux partition in Windows, it is likely to hose it up.  Best to use Linux utilities to manipulate Linux filesystems and partitions.  

Since you can't manage partitions that are in use, you will need to boot from Ubuntu installation media and then run GParted to do the Linux partition work.

---

### Post by oldfred on 2014-12-05
I cannot tell for sure from screen shots, but it looks like you have used all 4 primary partitions.
If you attempt from Windows to create another partition it will convert to dynamic partitions from basic. And that does not work with Linux nor even some Windows tools as it is a proprietary dynamic partition scheme overlaying the physical partitions. Some what similar to LVM in Linux.

You need to use 3 primary partitions, make the last primary partition as an extended partition and then you can have as many logical partitions inside the extended as you want. 

But moving partitions around can be risky so may sure you have really good backups of everything.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
       Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by jack117 on 2014-12-05
[B]That's exactly what it says (pls look at the new screen shots attached) I just creted a new unallocated sapce 113 GB 

[U]Now just tell me how can I make this as extended partition

[/U][/B]> **MAFoElffen said:**
> Since you can't manage partitions that are in use, you will need to boot  from Ubuntu installation media and then run GParted to do the Linux  partition work.                 [B]
Yes so I Resize/Shrink ubuntu partitions from Live USB tru GParted only, but some say do to it with Win 7 idk how?

and MS users say it drive cuz of C drive D drive..etc during format we call them partiton :KS:KS:KS 


[/B]

---

### Post by fantab on 2014-12-05
You can delete both /dev/sda3 ext4 and /dev/sda4 swap.
Make NTFS E drive as /dev/sda3 from unallocated space... ???Gb. (use gparted but when you are logged into Windows re-format the partition with windows specific tools).
Make an Extended partition from the remaining 'unallocated space', /dev/sda4. You will see that you still have unallocated space after the Extended partition... use the this space to create Logical partitions for Ubuntu '/', /dev/sda5 and 'swap', /dev/sda6.
Edit: An Extended partition is simply a Primary Partition acting as a container for Logical partitions.

Gparted tutorial:[ http://www.dedoimedo.com/computers/gparted.html]("http://www.dedoimedo.com/computers/gparted.html")

---

### Post by oldfred on 2014-12-05
You may be able to convert using fixparts.
But not sure it then UUIDs get changed and you have to edit fstab with new UUID and reinstall grub using live installer.
Again good backups are a must.

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

If it lets you I might convert both sda3 & sda4 to logical partitions. Then do then become sda5 & sda6, so any place throughout system using device like /dev/sda3 may need changing, but that is very few places.

---

### Post by jack117 on 2014-12-05
[COLOR=#000000][SIZE=3]I am so lost, I am only a beginner to Linux and ppl use words like LVM. So there is no other way other than completely deleting **/dev/sda3 ext4** and **/dev/sda4 swap** partitions? I thought, I could just shrink them and use **unallocated** space. It doesn't seem that simple [/SIZE][/COLOR]:-k
> **fantab said:**
> You can delete both /dev/sda3 ext4 and /dev/sda4 swap.

[SIZE=3]I will delete both [COLOR=#000000]**/dev/sda3 ext4 **and **/dev/sda4 swap**[/COLOR] from **Win 7 Disk management** will that effect my dual boot? I mean, will I see **GRUB2 **menu again? or Win 7 will boot normally[/SIZE]
[SIZE=3]**The link you gave was helpful **[/SIZE]:guitar:=d>  **[SIZE=3]and fixparts is confusing [/SIZE]**

[SIZE=3]Any other **Linux OS** you would recommend, apart from **Ubuntu**, as I have to delete it now. Which is good at customization and very cool.[/SIZE]

---

### Post by oldfred on 2014-12-05
I thought fixparts was just click a couple of boxes. If it will let you convert.

Do not delete Linux partition before you fix boot loader to boot Windows directly.
The grub code in the MBR, just looks into the Ubuntu partition for the rest of grub and the menu. If you delete that you get grub> and no boot at all.

Did you make a Windows repair CD or Flash drive. You should always have that and if you travel always have that with you. 

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by jack117 on 2014-12-05
> **oldfred said:**
> 
Do not delete Linux partition before you fix boot loader to boot Windows directly.


Yes I cannot delete partitions directly, before I used to have Win 7 and 8 dual boot and I just formated Win 8 drive.Still the dual menu existed, later I knew its not correct way and removed dual boot with Easy BCD. Can I will used Easy BCD to reset grub menu as well. 

I didn't have Boot-Repair in USB, cuz I already have Ubuntu in it. Now i will format my USB and have boot-repair and rest MBR and delete my partitions from Disk Managment :KS

---

### Post by fantab on 2014-12-06
Its ok to delete the Linux partition without fixing the windows boot, if you are going to install Ubuntu or any other distro immediately.

You can install Boot Repair tool in live ubuntu (that is one on USB after you boot with 'try ubuntu' option).

You can try [Xubuntu]("http://xubuntu.org/getxubuntu/") as an alternative to Ubuntu. Xubuntu is ubuntu with Xfce desktop and is faster.

---

### Post by jack117 on 2014-12-06
> **fantab said:**
>  You can install Boot Repair tool in live ubuntu (that is one on USB after you boot with 'try ubuntu' option).

[SIZE=3]Yes I did that now no need to have separate live ubutu and repair-disk

and I found a remedy to my problem I just resized **swap partiton** and growed **ext4 partion**. Now I can access ext4 from Win 7 tru _Ext2 volume partion_. I assigned letter **E: to ext4 partion**, Its just like I have 3 drives again. (just look at the attached screen shots u will understand) [/SIZE]
[ATTACH=CONFIG]258426[/ATTACH][ATTACH=CONFIG]258427[/ATTACH][ATTACH=CONFIG]258428[/ATTACH][B][SIZE=3]

Now I have a doubt, if I copy files and delete  them on E drive (which is  ext4) does it spoil my hard disk cuz Win 7  defragments while linux don't, so  is that a problem (or safe) to use this partion (for copying files and deleting)  from both Win 7 and linux??? [/SIZE][/B]

---

### Post by fantab on 2014-12-06
Can you read and write to ext4 partition from Windows? **Windows doesn't know linux parttions**... there is old driver with which you can read-only linux partition in Windows.
Why do you need to see Linux partition in Windows as E: ?
If you are looking for a partition to share data between Linux and Windows then such a partition should be formatted as NTFS, because linux can read and write to NTFS partitions.
Do NOT try to manage Linux partitions from Windows or with Windows tools... or else you will screw up and vice versa do NOT manage Windows NTFS partitions with Linux.

I see that you have not created an Extended Partition; well, with your current partitions setup you can work with it as it is. 
However remember that if you force any more parittion without an Extended partition your HDD will be changed to 'Dynamic Disk' in Windows and Linux will not read or access it.
Dynamic Disk is a windows proprietory, so be careful in the future.

Edit:
If I don't want any Extended parittion then I would go about it as follows:
/dev/sda1 Primary NTFS Win C: 100Gb
/dev/sda2 Primary NTFS Win D 300Gb (this is where I will store all my DATA, like documents, pictures etc and share it with Ubuntu)
/dev/sda3 Primary Ext4 Ubuntu '/' ??Gb (20-25Gb min)
/dev/sda4 Primary SWAP 2-4Gb

Then later we can automount that /dev/sda2 or Win D parittion at Ubuntu boot and use it as data partition.

On one of my notebook I have 500Gb HDD dual booting Windows and linux, and the parittion scheme looks like:
/dev/sda1 Primary NTFS Win C: 75gb
/dev/sda2 Primary NTFS Win D  75gb
/dev/sda3 Primary Ext4 XUbu '/' 30gb
/dev/sda4 Extended Partition
/dev/sda5 Logical Ext4 myDATA 316gb approx.
/dev/sda6 Logical linux_Swap 4gb

Partitions are as personal as your needs so think about your needs bearing in mind the ONLY 4 Primary Partition limit with MBR/msdos partition table.

---

### Post by jack117 on 2014-12-07
> **fantab said:**
> Can you read and write to ext4 partition from Windows? **Windows doesn't know linux parttions**... there is old driver with which you can read-only linux partition in Windows.

I guess u know this _Ext2 volume manager_ it enables to view Linux partion **ext4 **in **Windows 7** (yes we can uncheck a box were it says only read linux partion to abel to write) during installation of this program in windows it gives a option, force write to ext4 partion we check that box to write files to **ext4**. I copied few files as well.

> **fantab said:**
> 
Why do you need to see Linux partition in Windows as E: ?
If you are looking for a partition to share data between Linux and  Windows then such a partition should be formatted as NTFS, because linux  can read and write to NTFS partitions.

Like I said before, u saw from pics, I have 96 GB **ext4 **and 52GB **swap** I want to take away excess GB from both and use it in windows as E drive (I already have C and D drive). but as u can see I already have 4 primary partions. to create extended partition I have to delete both **/dev/sda3 ext4** and **/dev/sda4 swap** and again install updates from beginning. so I am looking to find other ways to use resize and manage **unallocated **space in win 7.

> **fantab said:**
> 
If you are looking for a partition to share data between Linux and  Windows then such a partition should be formatted as NTFS, because linux  can read and write to NTFS partitions.
Nope I am not looking for a partition to share data between Linux and  Windows (u know I can happily access my Win 7's C and D drives from linux so I don't need another drive again). I want that excess GB I have allocated to linux partions to be used in windows 7. 

> **fantab said:**
> 
Do NOT try to manage Linux partitions from Windows or with Windows  tools... or else you will screw up and vice versa do NOT manage Windows  NTFS partitions with Linux.
with Ext2 volume manager I can see and copy files to linux ext4. In linux I can already access my Win 7 NTFS C, D drives. **by NOT to manage u mean?? **

> **fantab said:**
> 
However remember that if you force any more parittion without an  Extended partition your HDD will be changed to 'Dynamic Disk' in Windows  and Linux will not read or access it.
Dynamic Disk is a windows proprietory, so be careful in the future.
I already mentioned this before, I resized my** ext4** and **swap** partions and gained **90 GB** **unallocated **that was placed after **swap** drive shown in black color in **Win Disk Managment**. When I tried to make **New Volume** with that **unallocated 90GB** with disk managment, windows displayed a warning it will convert to dynamic partitions from basic which will be no use. and from **linux GParted** it shows I already have 4 primary partiotions and I have to create extented partion. but to do that I have to delete both **/dev/sda3 ext4** and **/dev/sda4 swap.**

> **fantab said:**
> 
Edit:
If I don't want any Extended parittion then I would go about it as follows:
/dev/sda1 Primary NTFS Win C: 100Gb
/dev/sda2 Primary NTFS Win D 300Gb (this is where I will store all my  DATA, like documents, pictures etc and share it with Ubuntu)
/dev/sda3 Primary Ext4 Ubuntu '/' ??Gb (20-25Gb min)
/dev/sda4 Primary SWAP 2-4Gb

Then later we can automount that /dev/sda2 or Win D parittion at Ubuntu boot and use it as data partition.

yes this all happens by default. **But I spend less time on my linux** cuz it doesn't support many applications like MS office (liber is no good) CS6 and Browers extensions, _ubuntu for me is more like a chrome book_. I only use it for Browing internet opening multiple tabs won't hag up here, like in win 7 (I only have 1.5 GB RAM). So i feel that excess 90 GB allocated to it is of no use, I want to shrink it and either merge it with D drive in win 7 or use it as separate drive as new E drive in win 7.  

> **fantab said:**
> 
On one of my notebook I have 500Gb HDD dual booting Windows and linux, and the parittion scheme looks like:
/dev/sda1 Primary NTFS Win C: 75gb
/dev/sda2 Primary NTFS Win D  75gb
/dev/sda3 Primary Ext4 XUbu '/' 30gb
/dev/sda4 Extended Partition
/dev/sda5 Logical Ext4 myDATA 316gb approx.
/dev/sda6 Logical linux_Swap 4gb

Partitions are as personal as your needs so think about your needs bearing in mind the ONLY 4 Primary Partition limit with MBR/msdos partition table.to create** (/dev/sda4 Extended Partition) **like u, I have to delete **/dev/sda3 ext4** and **/dev/sda4 swap **of mine or else I cannot create a **extended partion. **The reason why I am using _Ext2 volume manager_ is tru this, I am able to access linux **ext4** partion to read and write.** But I don't know whether it is safe to do it? **I didn't know that I need to create a **exteted partion** while I installed ubuntu as I am all new to it.

---

### Post by oldfred on 2014-12-07
The general rule is not to write, but only read from system partitions with a different system. 

Windows often ends up having issues if you write too much directly from Ubuntu. And the Linux NTFS driver exposes all the hidden files & folders that Windows normally hides from you to prevent accidents. So with Linux it can be too easy to move or delete something essential.

The Windows tools have not been around long enough to know how well they work. I do not understand how they handle ownership & permissions which is vital for Linux to be safe on Internet.

You still can use fixparts to convert sda3 & sda4 to logical partitions and then with gparted expand the extended partition that is the container.

---

