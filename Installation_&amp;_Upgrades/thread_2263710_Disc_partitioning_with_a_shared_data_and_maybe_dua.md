---
title: "Disc partitioning with a shared data and maybe dual/multiboot system"
date: 2015-02-02
forum: Installation &amp; Upgrades
---

### Post by chaaderf on 2015-02-02
Hello!

I'd like to install linux on some boxes I'll get in near future and at the moment I'm planning how to create partitions wisely. But as I am a linux noob, I'd like to ask you advises too. What I want:

At the moment, I'm going to install only one operating system (linux) on each machine. But. I'd like to have an option to install more later to make the system dual/multi boot. In this manner, it would be nice to have a separate data partition so that all distros can handle the data. Also, if I decide to replace the operating system, this could help the installation as in successfull installation there wouldn't be a need to load personal files anymore.

So some questions:

[LIST]
[*]According to advices [here]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"), the first partition should be (possibly shared) swap. There is told in the guide that swap partition should be "swap size more than you have physical memory in order to use hibernation". But how much larger, actually? I noticed that in some older guides there are mentioned something like two times RAM, but some other guides suggest the size would be as large as amount of RAM. Which one is more precise? As far as I can see, the swap should be larger than RAM if there will be another distros on a machine...
[*]Do I need to set a separate boot partition or is it sufficient to have just root partition for each distro? How about the size of root partition?
[*]The data partition then... Where should that be mounted? On /home, /home/data, or somewhere else? And why? And filesystem format, can I use ext4?
[*]Thus far I know that the machines are quite old ones (almost 10 years or so). But in future note, is there any difference in doing this in UEFI system?
[*]Anything else I should take into account? **I've never done partiotioning manually**, so I'd like to get all your opinions and advices.
[/LIST]

And as a note: Yes, I know it is recommended to take a backup before installing any system, no matter does there exist a separate data partition or not. Also, there will not be Windows, ever. Only linux distro(s) if that matters.

Thank you for your help! ^^

---

### Post by ajgreeny on 2015-02-02
Do you really have to hibernate?  Linux usually boots so much faster than Windows that hibernation is seldom a big advantage over a shutdown/power-off.

I you don't need hibernation, forget the old rules about swap, and as long as you have 4GB ram or more limit your swap to 4GB (or even 2GB) as you are unlikely to use the swap in normal use.  On those older machines you may need to stick with the equal amounts of swap to ram as ram may be limited.

**DO NOT** make a separate /boot partition if you are using a normal desktop machine with legacy BIOS and msdos partition table, but you will need a small (100 - 200MB) partition of fat32 as an EFI partition if you actually use UEFI.  See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for details of how to deal with UEFI and GPT on a new machine.

If you choose to use encryption or LVM, neither of which are absolutely necessary, or in my opinion helpful, a separate /boot partition will be made automatically by the installer.  It is your responsibility then to make sure it does not get overfilled with new updated kernels as they are released.

The data partition is probably best as NTFS which Linux can read and write with no problems, or could be ext4, and I would mount it in a folder in /mnt in each Linux OS and then make soft links to a small /home partition (or /home folder within root) for all the main folders of data, ie the Documents, Pictures, Music, Videos, etc etc.
You can not use an ntfs partition for your /home in a Linux OS because it does not support Linux permissions, so though you can read and write to it, your shared ntfs partition will be for data only; all the configuration files and folders for applications of each separate OS will need to be either in the /home folder within root or on a separate small /home partition.

I have probably omitted a lot of info that may help you, but at least this shows you some of the potential pitfalls and warns you against trying certain things that the link you show suggests.  I certainly would stick to considering only separate root, home or data, and swap partitions, with an EFI on any new UEFI machines you may get later.  Forget about the possible use of separate /etc, /usr, /var, and so on; they do nothing more than complicate matters which is something you can do without.

---

### Post by MAFoElffen on 2015-02-02
The fllowing assumes all will be on one muli-boot box...

Really depends on:
- BIOS type of the main system 
 -- Legacy BIOS 
 -- UEFI)
- The OS'es you are planning for...
 -- Windows likes to be the first or near the root of the drive tree hiearchy.
 -- Linux and Unix don't care
- The boot manager
The above then leverages what the shared space's filesystem should be and where it may be located.
-- SMB and NTFS is fairly universal if you have a Windows member.
 -- If no Windows, and local then ext4 or ZFS.
 -- NFS is a faster share method than SMB shares.
I used to not separate out /boot or /home. Now I do it as habit. Just seems easier to recover if something goes south.

Swap can go anywhere. Assess what you really need. For desktop, rule of thumb is 1.5 times the installed memory. Some say that is overkill. But then again, I'm not a normal user with normal use or needs.

Server is a calculated guesstament based on installed, applications, services, and disk management types. I usually keep swap in it's own container (not in LVM nor RAID), on a separate disk. (but I have lots of spares).

---

### Post by yancek on 2015-02-02
If these computers are ten years old or almost that old, some of these options won't be available to you.  You're not likely to have 4GB of memory installed and I would agree that for normal users 2-4GB for swap is more than enough.  I don't know that it makes any difference if swap is on a primary partition or the first partition.  Someone else might have something to say about that.  I always have it on a logical partition.

There are valid reasons for having a separate boot partition.  If you don't know what they are, you don't need it.  If you're a fairly new user it will just add an un-necessary complication for you.

The root partition for your system files, 15-25GB should be more than enough.  It obviously depends upon what you have available and whether you expect to install a lot of software.

I'd also say to mount the data partition under the /mnt directory, that's what it's for.
If windows is going to fit into the picture somehow, you can create a data partition formatted ntfs as Linux can read/write to it.  If it's just going to be Ubuntu or other Linux systems, ext4 is a good choice.

If the computer hardware is nearly ten years old, UEFI won't be an option avaialble to you.
For detailed info on partitioning, the GParted Manual at the site below is as detailed as you can get.

[http://gparted.org/display-doc.php?name=help-manual](http://gparted.org/display-doc.php?name=help-manual)

---

### Post by Bucky Ball on 2015-02-02
You want the OS on the first partition, fastest part of the drive. This was rule of thumb back in the day, but disks are faster now. Old habits die hard. I always put the /swap last and at the end of the drive.

/swap needs to be no more than 2Gb if you don't hibernate. If you do, same size as installed RAM or larger.

---

### Post by chaaderf on 2015-02-04
Thank you for your answers. I'll return and ask more, if/when I have problems. ^^ :D

---

