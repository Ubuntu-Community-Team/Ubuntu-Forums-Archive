---
title: "Problem installing Ubuntu 8.04 to external USB HDD"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by spliffmonkey187 on 2008-05-27
Hi guys, first thank you for taking the time to read my post what ever help can be gleaned from you guys giving me a hand will be greatly appreciated. I will try keep the post clean and in order so that it can make sense to all of you and to anyone else that is in the same scenario that I am.

**_My Set-Up:_**

I have been trying to install ubuntu hardy heron (8.04) on my external usb hdd which i connect to my laptop. The external usb hdd is a Western Digital 250GB Passport. The laptop has Windows Vista (Home Basic) on it and an internal 80GB HDD (SATA). The external usb hdd (from now we will refer to it as ext-hdd) has been made into 2 ntfs partitions within Windows Vista, partition #1 = 37.4GB & partition #2 = 195GB. And before any of you ask, YES my laptop's bios does support USB booting and  the bios actually an automatically detect a bootable USB resource, but for safe measure i always go into the bios to make sure its in there and set to 1st boot device.

**_What I am trying to achieve:_**

Ok this is what i am trying to do. I want to install Ubuntu on partition #1 while keeping my MBR on the Internal HDD where Vista is safe and away from Ubuntu, this is so i can boot Windows when i do not have the ext-hdd plugged in. I also want to main the 195GB partition, as a common space where i can put files and other stuff from both Windows and Ubuntu, that way when i am in either OS they are readily accessible to both.

**_What have i done so far and whats the Problem?:_**

Alright if you are still with me thats awesome if not sorry for the long background on the situation. Ok now here is what i have done so far and what has happened thus. 

**Install time:**

I partitioned the ext-hdd into 2 partitions as shown above, i then restarted the machine from Windows Vista with the ubuntu CD in dvd-drive. The GRUB came up and i select Live User (since if i chose Install directly on the menu given my screens resolution goes insane, i get an ubuntu window that over stretches my screen...) Once Ubuntu loads (loads flawlessly) i see the USB partitions mounted and then select [INSTALL]. The Ubuntu Install begins to run and i get upto the [Prepare Disk Space] step.

On this screen i got two options (sorry i will try to upload screenshots later) [Guided -use Entire disk] under this i could see my two drives the ext-hdd and the internal hdd. Then the other option is [Manual].

(And yes i do not get the other 2 types of options that can apparently appear; [Guided Resize] and [Guided - use the largest continuous free space])

Now what i did was choose [Manual] in there i deleted the 37GB partition on the ext-hdd and it became free space. I then reformatted it as an ext3 partition. choosing its mount point to be / . I then got the "no swap partition selcted" error so i went back loaded up Firefox did some research on manual partitioning ( i am not too versed at doing it in ubuntu) So found out i needed to have 3 partitions for an install of ubuntu if i read it right they were as follows:-

ext3 /boot 100MB
swap swap 2GB
ext3 / the rest of the remaining memory of the 37GB partition.

So I stopped the instal process, went back into windows and divided up the 37GB partition into the 3 required partitions. I then rebooted into Ubuntu like i did before and got back to the manual partition phase, I deleted the partitions as usual then re made them so they would appear as required (above). i then clicked continue and get to step 8 of 8. There I clicked [Advanced] and set the device the boot loader needs to install to as (hd1) - that is what my ext-hdd turns up as. 

Ubuntu begins to install and i have no problems at all it then asks for reboot and i let it. I press F2 on the reboot to go into bios and i make sure the USB is bootable and the first boot device. I exit saving changes and let the machine go.

**_Now the long awaited problem:_**

Once i reboot i get in a nutshell the screen showing 

Grub Loading stage 1.5 please wait:
Grub Error 15

And thats it no options nothing. From what i have read this is to do with GRUB not installing right. But on my second attempt at this i told the boot loader to be installed on the /dev/sdb3 (the /boot partition) and i still got the same error. 

**_Help needed (;_; ):_**

So as mention my problem is that GRUB seems to not want to load up for some odd reason even with me telling the install to install it to the /boot partition. Has anyone got a solution for this, or if you have the same scenario setup as me how did you go about getting it to work?

Thanks guys for reading my long post if you need anymore info just let me know and i will be sure to post it up for ya in an instant. Actually i am gonna do a quick sudo fdisk -l in terminal and copy and paste the printout here for you guys so you can maybe have a better aspect of how my partitions are setup. I am halfway between beginner and intermediate user of ubuntu i run 7.10 on my desktop as main OS no Windows, so please do state terminal commands you use so i can learn better and be on the same page as you.

EDIT: Ok here it is my fdisk -l printout this might help out with any advice you guys can give on what i am trying to do.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b231b3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         131     1048576   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         131        9730    77100032    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4905    39394304    7  HPFS/NTFS
/dev/sdb2            4905       30402   204800000    7  HPFS/NTFS

** note that this time i have made the 2 partitions on the ext-hdd NTFS.

---

### Post by spliffmonkey187 on 2008-05-27
Ok status update. 

I made afew changes to my install/setup procedure.

**_In Windows_**:

I have pretty much done the same thing again but this time with a minor change. I have still got the two partitions but this time i have not made it into a "Simple Volume" so pretty much it is an unallocated space of 30GB and then the other remaining 190GB was made into a simple volume with an NTFS file system(this is the partition i hope to use as the "comm on storage" thingy I was talking about earlier. So pretty much here are the partitions on the ext-hdd

- 190GB "volume" NTFS
- 30GB Unallocated Space

**_In Ubuntu:_**

Ok now i got into Ubuntu Live User and this time i got the option [Guided -use largest free space] So i figured i might as well take the plunge and give it a shot. Turns out that it found the 30GB Unallocated space that i had setup in Vista, and just to make sure in Step 8 of 8 i made sure it was going to be doing those changes and partitioning to /dev/sdb (ext-hdd) i have now also told the boot-loader to go to (hd1) I think that is the right one for the ext-hdd and wont touch my MBR on the Internal drive and adversely affect Vista.

**_Here is my fdisk -l now_**

(it looks good since it made the ext3 and stuff all on its own and looks to be in order)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b231b3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         131     1048576   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         131        9730    77100032    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       26577   213476348    7  HPFS/NTFS
/dev/sdb2           26578       30401    30716280    5  Extended
/dev/sdb5           26578       30238    29406951   83  Linux
/dev/sdb6           30239       30401     1309266   82  Linux swap / Solaris

Its now asking me to restart i will let you know how it goes. Fingers Crossed.

---

### Post by spliffmonkey187 on 2008-05-27
Ok just got back from a quick recovery i had to do. i made a mistake in how i installed the grub. So ihad to restore Vista's MBR  , just got done with that and i am now going to try the following procedure from:

 [http://ubuntuforums.org/showpost.php?p=3713067&postcount=2](http://ubuntuforums.org/showpost.php?p=3713067&postcount=2)

I made a mistake using the above procedure (lol mistakingly did

setup (hd0)

I think it was supposed to (hd1) since i want to keep the MBR away from Ubuntu. But yeah that messed my MBR up and gave me a different GRUB Error this time Error 21. 

Back to trying to figure it out.

---

