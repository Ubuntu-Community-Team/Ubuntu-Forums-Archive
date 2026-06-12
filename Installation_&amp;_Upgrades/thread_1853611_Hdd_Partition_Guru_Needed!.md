---
title: "Hdd Partition Guru Needed!"
date: 2011-10-02
forum: Installation &amp; Upgrades
---

### Post by PcMojo on 2011-10-02
[SIZE=2]Hdd Partition Guru Needed!    

I fixed somebody else's PC that had a dual boot, xp & Ubuntu Lucid. I had to reinstall xp and it wiped out the MBR. I've dealt with this before several times but this time Ubuntu was gone and the Ubuntu partition was empty. I then installed Natty with the newer install program that ended up screwing everything up. [/SIZE] [SIZE=2]

It is 250Gb hdd and had sda1 ntfs for xp around 200Gb and sda2 40Gb for Ubuntu and 3Gb sda3 for swap, all primaries - no extended partitions. When I installed Natty in the "along side Windows" installation, it asked how many GB for Ubuntu and I again set it at 40. I should have realized something was wrong then, but I didn't. My ntfs is now 160Gb. It ended up adding sda4 extended partition containing a sda5 ext4 partition and sda6 swap, in addition to the other linux partitions and in the middle of the hdd. I unallocated the original sda2 and sda3 but they are at the end of the hdd. I would like the unallocated changed to ntfs and merged with the ntfs, but they are at opposite ends of the drive. I tried wiping out my ubuntu install from Ubuntu and from a live CD but it gives me an error because it says I'm mounted to that partition. (not sure why that would be with the live cd). [/SIZE] [SIZE=2]

I want to increase my ntfs partition back to 200Gb without trashing my xp install, it has taken me weeks to complete because it has six users that had to have many things installed individually. I have moved partitions before but it didn't always work out. Does anybody have any ideas on how I should proceed? I don't mind wiping out Ubuntu, it is easy to reinstall and I haven't done any customization to it yet. Should I delete everything that isn't ntfs and then use a utility to expand the ntfs to the size I want? If so which utility? And how do I delete Ubuntu if it prevents me from doing so because I am mounted? Should I move the ubuntu to the end of the hdd then extend the ntfs over the unallocated space? If so, how? If I move the sda4 extended partition will the sda5 and sda6 partitions move with it? ..... Help!!!![/SIZE]

---

### Post by coffeecat on 2011-10-02
First thing:

> **PcMojo said:**
> I tried wiping out my ubuntu install from Ubuntu and from a live CD but it gives me an error because it says I'm mounted to that partition. (not sure why that would be with the live cd).

You certainly can't wipe out Ubuntu from inside itself! The reason the Ubuntu partitions were locked in the live CD is because the live session automatically mounts the swap partition. Since it's mounted, it's locked and since it's a logical partition, the extended partition sda4 is locked, and since the extended partition is locked, so is the sda5 logical. Simply right-click on sda6 and choose "swapoff".

It's slightly difficult to follow exactly what your partition layout is like. Boot up a live Ubuntu CD, open Gparted and post a screenshot of the open Gparted window. And for good measure, open a terminal and post the output of:

```
sudo fdisk -lu
```

---

### Post by PcMojo on 2011-10-02
Following is fdisk: 

sudo fdisk -lu
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd14cd14c
Device        Boot      Start             End            Blocks   Id  System
/dev/sda1    *              63   332431919   166215928+   7  HPFS/NTFS
/dev/sda4       332433406   409593855      38580225    5  Extended
/dev/sda5       332433408   407515135      37540864  83  Linux
/dev/sda6       407517184   409593855       1038336   82  Linux swap / Solaris

The screenshot of Gparted is attached.

---

### Post by coffeecat on 2011-10-03
This is what you could do. Boot up an Ubuntu live CD and open Gparted from the live session. Right-click on the swap, sda6, partition and choose "swapoff". This will unlock the sda6 partition and the extended partition. Mark these for deletion in this order: sda6, sda5, sda4. Now apply that and you will end up with your XP partition and one big chunk of unallocated space.

You will now want to enlarge your XP partition. In Windows Vista and Windows 7 you can do this from within Windows and this is preferable. However, Windows XP doesn't have this ability and you will need to use Gparted. Fortunately, Windows XP seems to be more tolerant of being resized with Gparted than Vista or Windows 7, so if I was in your position I would use Gparted for this. Even so, you would be well-advised to take an image of your Windows partition before you resize it. If you don't have an imaging application in Windows, you can download the free version of Macrium Reflect for this. If you google Macrium Reflect Free, you'll find it. I've used it several times and found it to be reliable. Or, instead of Gparted, if you have a good 3rd party partitioning tool within Windows, you might prefer to use that to resize Windows. Whichever, it would be advisable to create an image first.

Once you have an enlarged Windows and contiguous unallocated space, you might want to consider setting up your Linux partitions in the live CD Gparted before starting the installer. In which case you choose the Advanced/Manual option in pre-11.04 installers such as Lucid, or "Something else" in 11.04. You can, I believe, create the partitions in the manual stage of the installer, but I simply prefer to use Gparted.

---

### Post by PcMojo on 2011-10-04
[SIZE=3]I didn't realize that the live CD mounted the swap partition. Your solution worked perfectly! :D  And thanks a million for pointing me towards Macrium Reflect. Awesome program! Great functionality and very intuitive! I was able to create a disk image within minutes after installing it. Although I haven't figured out how to reinstall the image, I'm still going through the help files. This program will save me thousands of hours of disinfecting computers. 

I am the computer geek of the family and everyone brings me their computers to fix. That's how I got started with Linux, by using rescue CD's. I'm now thinking of just buying a Terra-byte portable hard drive and putting images of everybody's hard drive on it. If windows gets infected (oh, who am I kidding; not IF but WHEN! ;)), I could just re-image and be done with it! This obviously, is the idea behind windows last know good configuration, and restore points, but viruses these days seem to know how to prevent these from working.

Thanks again CoffeeCat ):P

PcMojo (soon to be PcRe-Imager! :D)

BTW - I had a few problems with the ubuntu installation procedures and wanted to make some suggestions for the programmers. Do you know where I would do this? I've seen forums for bugs, but these problems aren't really bugs, they are clarifications to the user in the gui during the Ubuntu install process and an additional feature. Thanks again!
[/SIZE]

---

### Post by coffeecat on 2011-10-05
> **PcMojo said:**
> [SIZE=3] Although I haven't figured out how to reinstall the image, I'm still going through the help files.

You make a rescue CD (which is Linux-based!) from Macrium Reflect. This is bootable and you use this to restore an image back to a partition.

---

