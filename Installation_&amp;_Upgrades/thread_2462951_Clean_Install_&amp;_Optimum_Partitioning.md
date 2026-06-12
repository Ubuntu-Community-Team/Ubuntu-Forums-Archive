---
title: "Clean Install &amp; Optimum Partitioning"
date: 2021-05-31
forum: Installation &amp; Upgrades
---

### Post by erosman on 2021-05-31
Hi everyone

I am planning to clean install Ubuntu on a new laptop with 512gb SSD & 16gb RAM.

Before doing that, I would like to understand the optimum partitioning.

**Normal Installation -> Erase disk and instal Ubuntu**
[LIST]
[*]Is above the best option? *(I understand that it is the easiest option)* 
[*]What would be the outcome partition setup? 
[/LIST]

**Normal Installation -> Something else**
[LIST]
[*]What would be the optimum partition setup? 
[/LIST]

Thank you for the help

---

### Post by Impavidus on 2021-05-31
> **erosman said:**
> Hi everyone

I am planning to clean install Ubuntu on a new laptop with 512gb SSD & 16gb RAM.

Before doing that, I would like to understand the optimum partitioning.

**Normal Installation -> Erase disk and instal Ubuntu**
[LIST]
[*]Is above the best option? *(I understand that it is the easiest option)* 
[*]What would be the outcome partition setup? 
[/LIST]

This will create a small EFI partition and a big ext4 partition for everything else, assuming you install in UEFI mode (as you should on a new laptop). If you want an encrypted system, it will also create a /boot partition. I wouldn't call it optimum, but it's a good guess when the installer doesn't know how you want to use your system.
> 
**Normal Installation -> Something else**
[LIST]
[*]What would be the optimum partition setup? 
[/LIST]

Thank you for the help
Depends on how you want to use it. Some considerations:
How large do you want your root partition to be? I suggest around 30GB if you keep your documents somewhere else, more if you keep them in your root partition.
Do you want to keep space free for a second operating system, so you can dual boot?
Do you want a separate /home partition? This is where all your documents and settings go, so having it separate can make reinstalling easier.
Do you want a separate data partition instead of a /home partition? Simple data partitions can be shared between different Linux systems, a /home partition can't.
Do you want a swap partition or a swap file?
Any other partitions you want for special reasons?

---

### Post by erosman on 2021-05-31
> ... assuming you install in UEFI mode (as you should on a new laptop). If you want an encrypted system,....

My computing doesn't require file encryption. The normal login would be fine which I might even set to auto-login as I work at home 99% of the time.


> How large do you want your root partition to be? I suggest around 30GB  if you keep your documents somewhere else, more if you keep them in your  root partition.

I would like to keep my docs separate.
Some video guides suggest 40gb or 50gb for root `/` which is confusing.

> Do you want to keep space free for a second operating system, so you can dual boot?

Should I?
I am moving from Windows so I am not sure.
Last time I tried Linux was 20+ years ago (Slackware, Gentoo, Debian) as a dual boot with Windows but it was not easy those days and kernel panic caused me to leave it.
I am planing to get a laptop without an OS.
It is likely that I would need to run a Windows application few times a year (not available for Linux) for a very short time (fill out forms to submit).
Would an emulator or Wine do the job???

> Do you want a separate /home partition? This is where all your documents  and settings go, so having it separate can make reinstalling easier.

Indeed, that would be my choice. How large should it be?

> Do you want a separate data partition instead of a /home partition?  Simple data partitions can be shared between different Linux systems, a  /home partition can't.

Do you mean different systems running on the same machine or different machines?
I only use one laptop. On the other hand, in case of disaster, taking out the SSD and being able to read my documents would be advantageous.
I habitually backup files to external drives and prefer to keep the HD as empty as possible. My current laptop has 750gb HD and out of the 700gb usable space, 540gb is free.

> Do you want a swap partition or a swap file?

Some installation guides include one and some don't and I dont know what is best.

> Any other partitions you want for special reasons?                 

Nothing comes to mind.

Basically, I use a single laptop (with extra monitor) for normal computing plus programming (JavaScript). I don't play games.

---

### Post by slickymaster on 2021-05-31
Thread moved to **Installation & Upgrades** for a better fit.

---

### Post by grahammechanical on 2021-05-31
> It is likely that I would need to run a Windows application few times a  year (not available for Linux) for a very short time (fill out forms to  submit).
Would an emulator or Wine do the job???

If you have the install disc for that Windows application Wine might be useful. Remember, Microsoft does not give any assistance to the Wine Developers. Nothing is guaranteed. 

[https://appdb.winehq.org/](https://appdb.winehq.org/)

[https://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](https://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)

Before you ditch Windows completely make sure that you can do all the important stuff that you want to do with Linux applications or in Linux (through Wine) or by some alternative method.

Regards

---

### Post by GhX6GZMB on 2021-05-31
A 30 GB / partition makes a lot of sense.It isolates the OS from your user files, making upgrading MUCH easier.
Do you need Hibernate? If yes, you'll need a swap partition that's a bit larger than your RAM (eg, 17 GB).
The rest you can partition according to your user data needs (between users, or a separate video partition, or...)

---

### Post by Impavidus on 2021-05-31
> **erosman said:**
> 
Some video guides suggest 40gb or 50gb for root `/` which is confusing.I currently use a 32GB root partition, of which I use only 9.2GB for Xubuntu 20.10. I've got a separate /home partition. Wasting 20GB is no problem on a 320GB hard drive. Yes, it's quite old by now.
> 
Should I?
I am moving from Windows so I am not sure.People making a sudden switch to Linux often get disappointed. Wine may work, but that's not guaranteed. There are also virtual machines or you could keep an old spare computer running Windows. Dual booting can also refer to installing two Linux systems on one computer. Many people do that, for fun, to experiment or to have a spare system if one breaks.
> Indeed, that would be my choice. How large should it be?A /home partition is usually just all space that you don't need for something else. I don't know the rate at which you collect large files.
> 
Do you mean different systems running on the same machine or different machines?A simple data partition can be shared among multiple Linux systems installed on the same computer, dual booting. A /home partition can't. At least, not when you use the same user ID on both systems. This is because different Linux distros or versions will create incompatible config files with the same same.
> Some installation guides include one and some don't and I don't know what is best.A swap file is nowadays the default on Ubuntu. It's easier to resize or move. A swap partition can be used to hibernate. I don't think hibernation works with a swap file, but I'm not entirely sure. And a swap partition can be shared by multiple Linux systems dual booting on one computer. There may be a small difference in speed, but it's not very likely you'll actually use swap, so it doesn't really matter.

---

### Post by erosman on 2021-06-01
[B]Storing documents

[/B]Is it a good idea to create an NTFS partition and store documents there so that in case of need, it would be accessible by both Linux and Windows OS?
Would it affect the performance to read/write to NTFS?

---

### Post by oldfred on 2021-06-01
Only use NTFS partition if you have Windows. And make sure Windows fast start up is off, Windows may turn it back on with updates & then Linux NTFS driver cannot access it. You need Windows to run chkdsk or defrag ont NTFS partitions periodically, and you cannot do that from Linux.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

I find my own optimal partitioning obsolete after a few years. But I do not trust drives for much over 3 years as major working drive, so usually get a new drive and reallocated old drive to backup or misc use.

I suggest new users use default of / and if UEFI with gpt partitioning (which most systems are), an ESP - efi system partition. 
Anything beyond default requires Something Else install option.

Bit more advanced, better for larger total Linux partitions sizes, and often suggested is a separate /home partition and smaller / (root) partition. I use about 30GB for / partition and have about 9GB used with Kubuntu. But I include /home in /, and remove all snaps which now make root use larger. I put all data & some hidden folders like Firefox & Thunderbird profiles into data partition(s). About to convert to two or more data partitions. One with more unused space for data that varies a lot and others for some data I know will not change a lot.

An advantage of /home over data is that it then automatically adds mount of partition into fstab with correct ownership & permissions. If you create your own data partition you have to manually do all that and need to have some understanding of how much data you have or want to keep. So /home better for newer users, but those somewhat familiar with Linux.

---

### Post by Impavidus on 2021-06-01
Only use ntfs on the internal hard drive of your computer if it has Windows installed. Ubuntu can read and write ntfs, but not repair or defrag. If your system gets broken and can no longer boot, you can use a live disk to access the hard drive. If the computer is completely broken, you can take the hard drive out, connect it to a different computer (even a Windows computer) and use a Linux live disk to access it. There should be no need to access the hard drive in an emergency from Windows. So keep that disk you use to install Ubuntu. It is a great tool to have when you break the system.

Of course, for an external drive that you may want to use on Windows too, or if you install Windows alongside Ubuntu on the same computer, ntfs partitions make sense.

---

### Post by erosman on 2021-06-02
Thank you everyone for helping with my newbie questions.

I have read that hibernation can not be 100% reliable and hence it is off by default in Ubuntu.
Without hibernation, would **/swap** still be needed?
Some installation guides don't do /swap

What about **efi** partition?
Some guides mention efi partition around 100mb.

What about **/boot** ?
Some guides mention it.

On a 512 SSD, 16gb RAM, Ubuntu only set-up (not dual boot), would the following be optimal (for a starter):

```

/ efi                ?
/boot                ?
/sawp                8gb or 20gb?    
/                   30gb
/home               rest

```

When partitioning, does the order matter or is it ordered by the tool?
e.g. first /swap then / root then /home

---

### Post by oldfred on 2021-06-02
You can also use gparted to partition in advance, but must change device label or default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.

I always make the ESP first as that is an UEFI recommendation. And suggest 300 to 500GB. Windows typically makes it 100MB and if a small drive 100 will work. Larger gives some flexibility. I also use my ESP to download the UEFI updates as those must be in a FAT32 partition for UEFI on my system to read the update.

Its swap not /swap and 4GB is what many suggest for those wanting a partition. Default install now uses a swap file of 2GB. Swap is just if you load more applications than RAM has to prevent crash. I do not load a lot of apps and my old 4GB RAM system never used swap. 
When using swap partition I always put it at end of drive, right side in gparted. Then out of the way if I decide to move other partitions.

Most desktops do not need /boot, some server configurations may. It was used a lot back when BIOS had a hard limit that all boot files had to be in first 120/130GB of a drive. But that was 15 or 20 years ago.

I do not fully allocate my drives. I leave more unallocated on SSD. Examples, note total allocated is not total available, yet. 
Oldfred's partitions with new NVMe Feb 2020 UEFI 
[https://ubuntuforums.org/showthread.php?t=2437535&p=13934695#post13934695](https://ubuntuforums.org/showthread.php?t=2437535&p=13934695#post13934695)
Oldfred's partitions Dec 2015 has ESP & bios_grub
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

I used to have large data partition on HDD, with new NVMe drive I moved data to NVMe drive and use HDD for backup & test installs.

---

### Post by TheFu on 2021-06-02
Lots of excellent advice above.  We all do it a little differently, mainly because we all have specific histories and different uses.

The question is fairly common.  You'll make mistakes. Expect that. Every new install and we have a chance to do a little better than last time - which we do, but things will have changed a little, so we'll make fewer mistakes, but different mistakes.
A layout: [https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987)
With Reasons: [https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)

In those links, I'd change a few things today.
[LIST]
[*]The **/boot/efi** partition is 10x larger than needed.  **32MB** would be fine.  I'm currently using less than 7MB. The default seems to be 512MB - that's just crazy huge.
[*]The **/boot/** partition needs to be larger than the default, but not too large - **500MB** seems a happy middle ground. If you don't use LVM or encrypt the setup, then /boot doesn't need to be separate. It would be part of the OS, /.
[*]The **/** partition was 25G previously.  I'd make that **35G** with the push by Canonical towards more bloated snap packages.  Don't get me wrong, 25G is sufficient, but it isn't like you are hurting for storage. Running out of storage for the OS can be a huge hassle for many people. Go with 35G to have some breathing room.
[*]The **swap** partition should be **4.1G**.  I haven't changed by thoughts on that in a few years. If you don't hibernate, having larger really doesn't make sense.  All the old rules were made up when we had very little RAM.
[*]I'm a big believer in having a /stuff/ partition. That's were temporary files that never need to be backed up go. In general, on a laptop, those are media files that are copied over for entertainment during travel. They are not the primary copies. For media files, I keep those on network storage and handle the backups for those elsewhere. How big?  Guess that depends on your music and video tastes.  Since this is temporary and we can delete the partition and start over at any time, the size really isn't THAT important. 50G?
[/LIST]
With an SSD, I think it is smart NOT to allocate all the storage.  If you choose to use LVM, then the power of LVM comes from allocating only the storage that is needed for the next 3 months and leaving as much unallocated as possible. With LVM, we can increase the size of a "partition" on the fly - takes about 5 seconds and doesn't require any down time. With the unused space, under LVM, we can create snapshots which are handy for all sorts of uses - backups, pre-OS upgrades, pre-OS patching, or any other high-risk software install, configuration change, whatever. Snapshots are very handy, but we have to know they are possible, know how to use them, and have chosen LVM during install to even have a chance.  There's no easy way to add LVM to an OS post-install.  New disks can have LVM put down BEFORE the file systems, but not after - well - not without having to wipe everything first and start over. LVM brings flexibility, but there is a cost - added complexity.

IMHO, not encrypting a laptop is a huge mistake.  It is portable.  All your files will be on it.  You're at a coffee shop and leave your laptop at the table to get a refill. Someone walks by and grabs it when you aren't watching. Or if the drive fails - say you drop the laptop and all the bits bounce out of place (yes, that's a joke) on the SSD, whatcha gonna do?  Whole drive encryption means your files won't be on the internet or used for other purposes.  If there are any proprietary work files, then the storage must be encrypted, period.

Whole drive encryption means you can take it into any computer shop to have the hardware fixed, but not worry about your data being ransacked. Also, encrypted storage adds very little overhead, especially on an SSD. I'd bet you couldn't tell the performance difference, assuming you use the default whole-drive encryption.  However, encryption does mean that having excellent backups is mandatory.  But excellent backups are mandatory regardless.   Say we take our busted laptop in to get an internal wifi card replaced.  The tech would probably replace the card without checking, then attempt to boot. Well, there would be a "Enter encrypted password" Linux prompt, so the tech may get confused - and decide that clearly you need Windows10 on the machine so he can test it.  Whoooosh - Linux is gone.  That's were the backups would be handy.  There are over 100 other things that backups can solve that can't be solved any other way, easily.

---

### Post by erosman on 2021-06-02
Doesn't keeping parts of SSD unallocated, reduce the lifespan of the disk?

AFA I understand, the write times are limited on the disk and in order to increase life of the disk, different segments of the disk are written to which reduces the number of writes on each segment.

Having the whole SSD available, would increase the lifespan of the SSD.

AFA swap I think I read somewhere that LibreOffice tend to need a lot of RAM & swap.

[An introduction to swap space on Linux systems]("https://opensource.com/article/18/9/swap-space-linux-systems")  suggests 1.5times the RAM with hibernation or 0.5without.
I might be safe to keep it larger just in case.

From what I have gathered so far would the following be good enough?

[B]512 SSD, 16gb RAM, Ubuntu only set-up (not dual boot)
[/B]

```
efi                300mb
swap                24gb   
/                   40gb
/home               rest
```

---

### Post by TheFu on 2021-06-02
Nothing that is presented to the OS is the truth when it comes to quality SSDs.  Everything is virtual, so by not using some of the drive, we are actually allowing the on-SSD controller to use all the cells, including the unused ones, for load leveling. [https://www.extremetech.com/extreme/210492-extremetech-explains-how-do-ssds-work](https://www.extremetech.com/extreme/210492-extremetech-explains-how-do-ssds-work)  
> Unfortunately, we can&#8217;t go into too much detail on SSD controllers because companies lock down their various secret sauces. Much of NAND flash&#8217;s performance is determined by the underlying controller, and companies aren&#8217;t willing to lift the lid too far on how they do what they do, lest they hand a competitor an advantage.

Of course, if you are buying cheap SSDs - say $40/ 500GB, then all bets are off.

As for swap, believe what you want to believe.  I prefer to believe the virtual memory experts that I've met at work and in conferences over the decades. But I'm some nameless guy on the internet. No reason to trust me.
```
efi       [COLOR="#FF0000"]30mb[/COLOR]
swap      [COLOR="#FF0000"]4.1[/COLOR]gb
/         40gb
/home     [COLOR="#FF0000"]50G[/COLOR]/user

```

You can always increase /home later, if needed. **Just leave space to the right** and it is easy with a reboot, "Try Ubuntu", gparted, cycle.  With normal partitions, changing a partition table on the OS storage device has be accomplished through a *Try Ubuntu* flash drive boot since partitions on the disk cannot be mounted and modified at the same time.

OTOH, if you use LVM, then resizing larger is a 5 second command while the system keeps running.  
Resizing smaller will probably need a reboot and *Try Ubuntu* from flash media.

But remember that SSDs present virtual cells to the OS to make up the disk.  Don't expect the cells used to be side-by-side for very long.  Think of it like OSes do for Address space layout randomization.  [https://en.wikipedia.org/wiki/Address_space_layout_randomization](https://en.wikipedia.org/wiki/Address_space_layout_randomization)  SSDs are like that and have been for over 5 yrs, perhaps 8 yrs, according to my information.  But I'm just some random guy on the internet.

---

### Post by Impavidus on 2021-06-03
If you don't use hibernation, have more than 4GB of RAM and aren't editing videos, you only use swap as a warning. When you run out of memory, everything will slow down and you have time to close some applications. Usually you close the application that has a memory leak. Without swap, random applications would crash.

---

### Post by erosman on 2021-06-03
Thank you for all your help.

There doesn't seem to be a consensus when it comes to partitioning.


[Beginner's Guide: How To Install Ubuntu Linux 18.04 LTS](https://www.forbes.com/sites/jasonevangelho/2018/08/29/beginners-guide-how-to-install-ubuntu-linux/) states:

> Now you will need to create 3 partitions, beginning with a "Swap Area."
As a rule of thumb, you'll want it to be slightly larger than the amount  of RAM you have in your PC. I have 16GB of RAM, so I'm creating a 20GB  (or 20000MB) swap partition.
...
You may be required to create an "EFI Partition" as well, and if so Ubuntu will tell you.
If you're asked to create one, just follow the same procedure as all other partitions. Make it 250MB.


Opinions on EFI partition size vary from 30mb to 250mb.

Opinions on swap partition size vary from 4gb (without hibernation) to 24gb (with hibernation).

Opinions on / partition size vary from 20gb to 40gb.

/home partition size is not a problem as I imagine if not all the SSD is allocated, it can be extended if needed.

---

### Post by Impavidus on 2021-06-04
There's a lot of rubbish on the web. There's also a lot of outdated info. I would have more confidence in Ubuntuforums than in a random blog written by someone admitting to be new to Ubuntu, in particular when you've received replies from multiple people on your thread. There appears to be some consensus here. And you won't notice if one of the small partitions is a few GB larger than needed. It's only a few percent wasted storage space.

---

### Post by erosman on 2021-06-06
Will / only contain Ubuntu?
Where do applications get installed, in /home or / ?

---

### Post by TheFu on 2021-06-06
> **erosman said:**
> Will / only contain Ubuntu?
Where do applications get installed, in /home or / ?

Linux File System Hierarchy Standards: [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)
There's a nice table there.

---

### Post by erosman on 2021-06-06
> **TheFu said:**
> Linux File System Hierarchy Standards: [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)
There's a nice table there.

Are those automatically created?
Should I create /var /usr /etc ........ etc?

---

### Post by TheFu on 2021-06-06
> **erosman said:**
> Are those automatically created?
Should I create /var /usr /etc ........ etc?

That is a judgement call.  It depends.  In general, no, but you could.  
For example, here's one of my real systems (**df -Th** output stripped of gunk):
```
Type  Size  Used Avail Use% Mounted on
ext4   32G   17G   14G  54% /
ext2  720M  162M  522M  24% /boot
ext4  459G  416G   44G  91% /Backups
ext4  173G  127G   37G  78% /var/lib/libvirt
ext4   59G   14G   42G  25% /var/lib/lxd
zfs    13G  937M   12G   8% /var/lib/lxd/storage-pools/lxd/containers/pihole
```
It boots with legacy BIOS, not UEFI.  This is an SSD system, with backups to a HDD.
[LIST]
[*]/ is 32G in size.  That's plenty to hold everything - for me. I don't install every GUI app there is. I know what I like and remove stuff I don't like. 
[*]/boot is a little large, but I'd been burned on another system with too small /boot/ and got into some kernel update issues. This machine has never come close to using 500MB for /boot.
[*]/Backups - are on a completely different HDD.
[*]The other areas under /var/lib/.... are for special needs.  libvirt is the default location for KVM/QEMU virtual machines. I actually don't use much of that storage because I prefer to provide each VM with direct access to a logical volume, which doesn't show up in the **df** output. There are 15 LVs on this box for 10+ virtual machines.  I removed the first column in the table above, which showed LVs, not partitions, trying to limit confusion.  LVs don't look like partitions.
[/LIST]

So, the answer is "it depends."  My prior answer is a best guess at what would be low risk, but not wasteful, for most desktop user needs with a 20.04 or later install.

Don't confuse partitions with directories.  Most of the time, they aren't really tightly coupled.  As long as files "appear" in the correct directory, the underlying storage and mounts just need to be native Linux file systems for the most part. There are a few exceptions, like /boot/EFI must be FAT32 and external data storage may be NTFS, if you like, but your HOME directory cannot be NTFS/FAT32/exFAT, at least not currently.

_Update_: Just to clarify, in the table above, /var is part of /.  It is only the very specific, deeper, areas that have other mounted storage.  Below, oldfred shows a little cleaner, typical, setup using UEFI boot, no LVM, and /home is on / too, but most of the data files are placed on the /mnt/data partition. I'd guess symbolic links from places inside his HOME to that other location ~/Documents ---> /mnt/data/Docs or similar is being used.

---

### Post by Impavidus on 2021-06-06
> **erosman said:**
> Are those automatically created?
Should I create /var /usr /etc ........ etc?

They are automatically created as directories on the root partition when  you install Ubuntu. If you really wish you can put /var on a separate  partition, but on typical systems that doesn't really serve a purpose.

---

### Post by oldfred on 2021-06-06
Apps are installed in multiple places. 
I like to install zim to keep my notes on what I comment here & terminal commands as I do not remember all the extra parameters or exactly how they are used for every command.

[FONT=monospace][COLOR=#54ff54]**fred@z97-focal-kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ whereis zim [/COLOR]
zim: /usr/bin/zim /usr/share/zim /usr/share/man/man1/zim.1.gz

You can install games in /home.

I prefer to just have ESP, / (more than one) on SSD & copies, data , test installs HDD. My other system has larger NVMe SSD & I have moved data to NVMe drive. I keep /home inside / as it is tiny when all data is in data partition. But I immediately remove all snaps which are larger versions of apps. And for a few apps then  install the .deb versions.
So I have systems with similar, but different partitioning. This also shows another 128GB flash drive's data partition.

```
 fred@z97-focal-kubuntu:~$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda6      ext4       24G  9.3G   14G  42% /
/dev/sda1      vfat      499M   16M  484M   4% /boot/efi
/dev/sdb4      ext4      385G  131G  235G  36% /mnt/data
/dev/sdc4      ext4       94G   33G   56G  38% /media/fred/data128
```[/FONT]

---

### Post by erosman on 2021-06-07
As mentioned I am new to Linux/Ubuntu so when I get varying opinions, I get even more confused. 

So far... I understood that for a **basic** set-up I would create 4 partitions:
**efi** + **swap** + ** /** + **/home**


AFA their sizes, I get varied opinions, even here in this topic.

**efi** has been suggested from
TheFu      30mb
oldfred   512mb

**swap** has been suggested from
oldfred    2gb
TheFu      4gb
ml9104    17gb

**/** has been suggested from
ml9104    30gb
oldfred   30gb
TheFu     40gb

Regarding **efi**, the space is small and it doesn't really matter if it is more that needed. I guess 100mb (as suggested in a video tutorial) would be safe.
Regarding **swap**, I don't know if I will use hibernation or not, but to avoid having to reformat, it would be safe to go for 20gb.
Regarding **/** , I guess 40gb should be safe.

I am still unsure where the installed applications go. Do they go in **/** partition or in **/home** partition (it doesn't matter about the sub-directories).

&#128073; The reason I ask is that, if I want to replace/reinstall Ubuntu, would I also have to reinstall applications as well or not?

---

### Post by TheFu on 2021-06-07
The different opinions is because we all have different experiences.

As for swap, if you have 16G of RAM and plan to hibernate, having 16.1G of swap in a separate partition is the "correct" answer.  If you don't hibernate, 12G will be wasted, unnecessary. Not the end of the world.

The default Ubuntu package manager will install files in 3 places.
[LIST]
[*]/usr
[*]/etc
[*]/var
[/LIST]
Typically, those will be part of the / partition.

HOME - which doesn't HAVE to be /home - gets personal data and personal settings.

If you like, you could make each partition 100GB "to be safe".  It would be crazy inefficient, but you could do it and the FAT32 tools will freak out, since MSFT says FAT shouldn't be larger than 32GB.

Reinstalling is 15 minutes. Not the end of the world if it has to be done.  Why not plan to spend an hour, trying 4 different installs, see what happens?  We've shown the commands to check sizes above - run those commands after each install - see what you can see. Then decide for yourself.  No need to be paralyzed.

---

### Post by VMC on 2021-06-07
My swap partitions is 2gb, since I don't load a ton of heavy programs. My EFI is 550MB. Read this regarding EFI size:
[https://askubuntu.com/questions/1313154/how-to-know-the-proper-amount-of-needed-disk-space-for-efi-partition](https://askubuntu.com/questions/1313154/how-to-know-the-proper-amount-of-needed-disk-space-for-efi-partition)

There is some distros that require a larger EFI. They place kernels inside EFI. But if you plan to stay with Ubuntu/debian your safe with the default 100MB.

Everyone has own opinion regarding partitions. I keep everything inside "/". In time you will figure it out.

---

### Post by Impavidus on 2021-06-07
> **erosman said:**
> As mentioned I am new to Linux/Ubuntu so when I get varying opinions, I get even more confused.When you get varying opinions from experience users, it usually doesn't really matter.

> I am still unsure where the installed applications go. Do they go in **/** partition or in **/home** partition (it doesn't matter about the sub-directories).

&#128073; The reason I ask is that, if I want to replace/reinstall Ubuntu, would I also have to reinstall applications as well or not?

The applications you install from the official repositories (I rarely install anything from other sources) get installed on your root partition. Their files get spread over /var, /etc and /usr, usually. /home is only for user files.

When you replace or reinstall Ubuntu, you have to reinstall the applications too. A different version of Ubuntu comes with different versions of applications and different versions of their supporting libraries. Reinstalling the applications can be automated, if you wish. I don't, as the applications can be reinstalled with a few clicks and it's only needed once every 2 years.

---

