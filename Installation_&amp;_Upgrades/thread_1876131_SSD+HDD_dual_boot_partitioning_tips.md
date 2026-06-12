---
title: "SSD+HDD dual boot partitioning tips?"
date: 2011-11-05
forum: Installation &amp; Upgrades
---

### Post by mace2 on 2011-11-05
Hi all,

I have these drives:
- 120GB SSD
- 640GB 7200rpm HDD
- 2TB 5400rpm HDD (backup)

I am trying to figure out how best to partition my SSD and 640GB HDD for Ubuntu and Windows 7.

I use Ubuntu for work primarily and have about 80GB of data. I only work on maybe 10-20GB at once, so I could offload some of the data to the 640GB HDD and put the data I need on the SSD occasionally? That way I could have Win7 boot on the SSD as well.

Or should I just put Ubuntu wholly on the SSD and Win7 on the 640GB HDD?

Ideally I wouldn't have to move any of my work data around and I'd get the Win7 speed boost... any tips are appreciated, thank you.

---

### Post by darkod on 2011-11-05
I haven't used UEFI so you probably know more about it than me.

However, I can help with the win7 programs dilemma. In windows it's very easy to change the default location for the Program Files. There is no problem to have them on the 640GB disk, while having win7 installed on the SSD.

I don't know how to change the default program location for ubuntu. Not sure if it is the /usr folder. Once you know which is it, there is no problem creating a partition on the 640GB for it and mounting it as /usr (for example).

100GB for ubuntu is quite large, but then again you probably know what you need much better than me.

Start doing the math, how to utilize the SSD to maximum, believe me it's worth it. Ideally win7 + ubuntu installations on it, and as much programs as you can fit, again for both OSs.

The 640GB for data and rest of the programs that can't fir on the SSD. If in those 100GB stated you have data files, not program files, that can go to the 640GB too.

PS. Depending how you use win7, search google for ways to slim it down before installation. Windows as windows, has loads of s**t you will never need, and even if you remove those parts it does not give you the space back.
However, if you use vLite and remove windows components BEFORE, recreate a DVD from the slimmed version, it never takes so much space on your SSD to begin with. For example, lets say you install the english version. There is a component called Languages (and most times you use only english, will never change it) that takes more than 1GB. The same goes for Printer drivers. Huge space, thousands of drivers, and you need how manu, 3-4?

I have slimmed Win7 Ultimate this way and installed in VBox to see the result. Astonishing. Not counting the page file, the full install (I mean the full slimmed down install, but fully functional, just removed components I will never use) took only 3.1GB installed. That's crucial for SSD IMHO.

---

### Post by MAFoElffen on 2011-11-05
> **mace2 said:**
> Hi all,

I have these drives:
- 120GB SSD
- 640GB 7200rpm HDD
- 2TB 5400rpm HDD (backup)

I am trying to figure out how best to partition my SSD and 640GB HDD for Ubuntu and Windows 7.

I use Ubuntu for work primarily and have about 80GB of data. I only work on maybe 10-20GB at once, so I could offload some of the data to the 640GB HDD and put the data I need on the SSD occasionally? That way I could have Win7 boot on the SSD as well.

Or should I just put Ubuntu wholly on the SSD and Win7 on the 640GB HDD?

Ideally I wouldn't have to move any of my work data around and I'd get the Win7 speed boost... any tips are appreciated, thank you.
Good points on Post 2... If you look at my sig line- I have a little broader perspective on this.  Having both you sys'es on the SSD would increase startup and application speed. Store your data on other drives is fine and normal. If your data is in large files, then your read writes will be a little slower.

My recommendations for things like this is to load Win7 first... Windows systems like to operate near the lower parts of a disk and they do weird querky things when not.  I start my Win partitions on sector 2.  Giving them a small buffer of unallocated space before that partition -- has saved me from previous nightmares in multi-boot systems.

Linux (Ubuntu) doesn't care where it's loaded and it will load from either a primary partition or a Logical partition- which comes in handy.

Third part of your plan is where your data id going to reside. For multi-boot systems, I pick a storage area that has a common filesytem that is recognised by all my installed OS'es. That is if the filesystem resides locally. Network storage can be anything as long as it reads the network share. Working with data stored locally is faster than retrieving data from Networks Shares.  

This box I writing this from has NTFS, ZFS, Ext4 and FAT32... My install of Ubuntu can read/write to all those. Unix, Unix with ZFS and NTFS. Win7 --> NTFS and Fat32. As you can see, My choice for a shared data storage is in NTFS partitions.  I have that area mounted at bootup in Linux and Unix / Win already see's it at boot.  

for Printers I have Ubuntu set for one locally and 3 on network shares... but my best printer is a network all-in-one that isn't supported by CUPS.  If I need something printed on that printer, I usually already have the document in shared space, but have to print it from Windows (Vista or Win7).

One other thing you can figure in, is that with Windows, programs and such burn up a lot of room.  If you could factor in the some of those could be installed on another disk or partition.... I have another disk that I install my windows programs on to.

I hope that helps...

---

### Post by recluce on 2011-11-06
First of all, be sure to align your SSD correctly, otherwise you loose more than 50% of your write speed in many situations. If you google or search the forums, there are plenty of how-tos on how to do that. Depending on the model, even the 2TB drive might alignment (all "advanced" format drives that use 4k sectors internally, like WD Caviar Green).

Other than that: if you partition manually, be sure to include a Windows system partition (not the same as your Windows partition!) at the beginning of your drive, this only needs about 150MB.

```

A possible layout for the SSD for non-UEFI layouts:

Part #1  NTFS Primary  150 MB  Windows System
Part #2  NTFS Primary   50 GB  Windows 7
Part #3  Extended Partition
Part #5  EXT4 Logical   20 GB  /root
Part #6  EXT4 Logical  ~50 GB  /home


```

For UEFI, you need a small partition at the beginning of the drive for UEFI bootloader code. Google this, I am no specialist for UEFI...

SWAP partition is debatable. If your system swaps infrequently, put SWAP on the HDD and save valuable SSD space. If you have a swap-intensive system, put some swap space on the SSD and resize accordingly.

Notes: This setup assumes Windows program files on SSD, data and documents on the HDD. Also, it makes sense to have something like /home2 on the HDD and symlink there from your SSD for data folders that are less speed-critical.

For example:

```

640 GB hdd layout:

Part #1  NTFS Primary  Windows Data
Part #2  EXT4 Primary  /home2
Part #3  NTFS Primary  Shared Data

```

Partition sizes according to your needs

---

### Post by darkod on 2011-11-06
> 
Other than that: if you partition manually, be sure to include a Windows  system partition (not the same as your Windows partition!) at the  beginning of your drive, this only needs about 150MB.


Can you do this manually? I was under the impression that if you have win7 partitions prepared in advance, and just select the destination during the install, it will put the system files on the same, not on the smaller one.

When I was installing on my netbook, I did not have them prepared in advanced. So when the win7 installer is used to create the partition from unallocated space, you tell it to be for example 50GB, it cuts out small space and creates the system partition itself.

But on my desktop I just formatted the existing ex-vista partition as ntfs, and then selected it as destination partition for win7, the installer did not create the small one.

From that example, and I have used it later, I figured out that if you prepare the partition in advance, the small one will not be created and you can save one primary partition if that's important to you.

---

### Post by Matti L on 2011-11-06
> **darkod said:**
> From that example, and I have used it later, I figured out that if you prepare the partition in advance, the small one will not be created and you can save one primary partition if that's important to you.
I would prefer not having system partition and I don't think it hurts. I'd probably partition like this:

120 GB SSD:
Part #1 60GB Primary NTFS C:
Part #2 60GB Primary EXT4 /
(50/50 for Windows and Linux, but I think Ubuntu could be just 10 GB if you don't need much extra programs or anything)

640 GB HDD:
Partition how you like, but /home and swap would be here and maybe a shared data partition (NTFS).

That is if your data is on the home partition as I understood it.

---

### Post by darkod on 2011-11-06
> **Matti L said:**
> 
(50/50 for Windows and Linux, but I think Ubuntu could be just 10 GB if you don't need much extra programs or anything)


My newest default install of 11.10 32bit + Netbeans IDE + Oracle Java JDK7 is barely 2.7GB if I'm not mistaken. Not at home now to check immediately.

Even with bunch of added programs Linux is never as space demanding as Windows. At least that seems to be the rule so far. Of course, the OP knows best what he needs to use.

---

### Post by Basher101 on 2011-11-06
This is some neat information as i will very soon (in 1-2 months) get a UEFI gaming setup with 1,5 TB HDD and a 120 GB SSD. After some googeling i found this page [http://blog.superuser.com/2011/05/10/maximizing-the-lifetime-of-your-ssd/](http://blog.superuser.com/2011/05/10/maximizing-the-lifetime-of-your-ssd/) seems very helpful to keep your SSD working for as long as possible (so we dont have to buy a new one every 2 years..)

---

### Post by Matti L on 2011-11-06
> **darkod said:**
> My newest default install of 11.10 32bit + Netbeans IDE + Oracle Java JDK7 is barely 2.7GB if I'm not mistaken. Not at home now to check immediately.

Even with bunch of added programs Linux is never as space demanding as Windows. At least that seems to be the rule so far. Of course, the OP knows best what he needs to use.
Yes, it's true that Ubuntu and most Linux distros won't take much room. 2-4 GB seems to be pretty standard, but I have managed to run out of space on a 8 GB / partition so if you have a lot of space then be generous with it. ;)

---

### Post by darkod on 2011-11-06
> **Matti L said:**
> Yes, it's true that Ubuntu and most Linux distros won't take much room. 2-4 GB seems to be pretty standard, but I have managed to run out of space on a 8 GB / partition so if you have a lot of space then be generous with it. ;)

Probably I should have made my previous post longer. My main point was that splitting it 50/50 might be too generous to Ubuntu and too little for Windows. Again I say, the OP knows best what applications are needed in Ubuntu and how much space they take.

But in order to have as many Windows programs on the SSD too, it's better not to give too much space to Ubuntu unless needed.

Too bad Windows doesn't have a clue for linux partitions and LVM, otherwise LVM is a great thing for cases like this. You can just keep expanding the partitions on the fly, until you reach the total of the disk of course.

Like this, between ntfs and ext4, you have to do a lot of math to make the best decision in advance.

---

### Post by Matti L on 2011-11-06
> **darkod said:**
> Probably I should have made my previous post longer. My main point was that splitting it 50/50 might be too generous to Ubuntu and too little for Windows. Again I say, the OP knows best what applications are needed in Ubuntu and how much space they take.

But in order to have as many Windows programs on the SSD too, it's better not to give too much space to Ubuntu unless needed.

Too bad Windows doesn't have a clue for linux partitions and LVM, otherwise LVM is a great thing for cases like this. You can just keep expanding the partitions on the fly, until you reach the total of the disk of course.

Like this, between ntfs and ext4, you have to do a lot of math to make the best decision in advance.
True.

---

### Post by mace2 on 2011-11-06
Thanks for the suggestions everyone. I am going to split Linux/Windows on the SSD as recommended, and have an extra /home2 and NTFS partition on the 640GB drive.

Can I just install Win 7 on the SSD as normal, and then have Linux resize it to make space for itself? Or will this mess up because my mobo uses UEFI?

Thanks again.

---

### Post by darkod on 2011-11-06
Since you are starting with a fresh install I never recommend letting win7 take all the disk. Why resize when you plan to dual boot from the start?

With the win7 installer (or before that, using ubuntu cd in live mode and Gparted) create the ntfs partition for win7 with the size you plan to allocate to it. Leave the rest of the disk as unallocated. DO NOT create a second ntfs partition.

Then when installing ubuntu just use the automatic option or manual for creating the partitions yourself from that unallocated space.

Shrinking the win7 partition might break it sometimes, no need to do it in your situation.

---

### Post by mace2 on 2011-11-06
> **darkod said:**
> Since you are starting with a fresh install I never recommend letting win7 take all the disk. Why resize when you plan to dual boot from the start?

With the win7 installer (or before that, using ubuntu cd in live mode and Gparted) create the ntfs partition for win7 with the size you plan to allocate to it. Leave the rest of the disk as unallocated. DO NOT create a second ntfs partition.

Then when installing ubuntu just use the automatic option or manual for creating the partitions yourself from that unallocated space.

Shrinking the win7 partition might break it sometimes, no need to do it in your situation.
Thanks, I will try this tonight.

---

### Post by MAFoElffen on 2011-11-06
> **Matti L said:**
> Yes, it's true that Ubuntu and most Linux distros won't take much room. 2-4 GB seems to be pretty standard, but I have managed to run out of space on a 8 GB / partition so if you have a lot of space then be generous with it. ;)
Well, another twist to this is my Ubuntu install includes Netbeans IDE, Eclipse, Monkey Studio and Solaris Studio. It also includes an assortment Debuggers, VirtualBox and VMware for testing.  I keep non-essential data on other disks and network shares (Servers, NATs and RAID servers)... Then I have an assortment of editors and browsers.  I have one server with Apache and Tomcat Server to test on... Where i used to that all through local://

I keep an eye on and manage where things are.  With what the OP says he has installed (or planned), that basically sounds like what he is getting into right?

My local installed Ubuntu is currently at 160GB used.

The twist on this, is that even though I also run Win7 on that disk, Vista on another... I've only access those systems once each every 6 months to make sure they get updated... and every blue-moon, if I have to use Fiddler Web Debugger, which only runs on Windows. If i found da linux substitue for that, my Windows installs would probably be orphaned.

---

### Post by recluce on 2011-11-07
> **mace2 said:**
> Thanks for the suggestions everyone. I am going to split Linux/Windows on the SSD as recommended, and have an extra /home2 and NTFS partition on the 640GB drive.

Can I just install Win 7 on the SSD as normal, and then have Linux resize it to make space for itself? Or will this mess up because my mobo uses UEFI?

Thanks again.

For UEFI it is recommended to install Windows **first**, the opposite of the procedure for a BIOS based system. I would also recommend to limit the size of the Windows installation during install. 

If you need to resize your Windows partition, best do it from inside Windows. While I have never had any trouble using GParted to resize a Windows partition, to many reports exist about this to ignore.

---

### Post by recluce on 2011-11-07
> **Matti L said:**
> Yes, it's true that Ubuntu and most Linux distros won't take much room. 2-4 GB seems to be pretty standard, but I have managed to run out of space on a 8 GB / partition so if you have a lot of space then be generous with it. ;)

It baffles me that your installations are so small :o

My root partition (home is on a separate partition) is currently at 10 GBs used. I guess it all depends on what you do with your machine. I recommended 20GB to be on the safe side, in a pinch I would shrink my root to 15GB.

---

### Post by oldfred on 2011-11-07
There are several UEFI bugs that are not well reported, since most new users either give up or convert back to BIOS.

UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be at least 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB. Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell]("https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell")

[SOLVED] Win 7, Natty dual boot on UEFI sort of working 
[http://ubuntuforums.org/showthread.php?t=1753717](http://ubuntuforums.org/showthread.php?t=1753717)
[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)

Good info on SSDs
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
Grub2 efi info ArchLinux
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

---

### Post by recluce on 2011-11-07
@oldfred: thanks for the very helpful and detailed link collection about UEFI!

---

