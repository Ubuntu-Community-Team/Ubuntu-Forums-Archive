---
title: "can't find my partitions"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by watchman323 on 2010-11-11
I am using my flashdrive to install.  I allocated 200gb for window 7 ult and used partition magic to format the rest to ext3 and swap for DISK 1.  But when I try to install Ubuntu,installation can't seem to find the ext3 or the swap.  It only sees my other drive in RAID 1.  
my harddrive setup

Disk 1(RAID ready)
NTFS 100 mb - System 
NTFS 195.21 GB
EXT3 253.88
Linux Swap 16.46 GB

DISK 2 (RAID 1)
NTFS931.31 

Thankyou

---

### Post by ronparent on 2010-11-11
When I last checked, partition magic hadn't been updated since released for 
win xp. You might want to boot to the live cd and check out what the partitions look like with gparted. Which release of Ubuntu are you trying to install (ie 9.10, 10.04, 10.04.1, 10.10 etc)?

---

### Post by watchman323 on 2010-11-11
partition magic can do ext 2 and 3, but I still can't see all partitions when using live cd.  live cd shows my RAID 1 drive and not even my disk 0 or the space I allocated for ubuntu.  I tried using wuinst.exe too but when I rebot my ubuntu says no root (i think).

---

### Post by ronparent on 2010-11-11
The Partition Magic I am familiar with was bought by Norton and has never been updated. It should not be used with vista, win 7 of for creating partitions for any current release of Ubuntu.

You don't appear to know how raid 1 works. If, as I think, you installed win 7 to a raid 1, the win 7 install was mirrored between disk 1 and disk 2. That is a raid set. Somehow you seem to have partitioned disk 1 to provide separate partitions to install Ubuntu to. If so, the raid set is no longer valid.

The better approach, for many reasons, would have been to use the built in win 7 disk manager to create unallocated space for installing ubuntu to. If win 7 was installed to a raid 1 it and all its partitions would have been mirrored to disk 2. 

Win 7 probably had at least two primary partitions when installed to begin with. The next step would have been to use gparted in the live cd to create an extended partition in the raid 1 for Ubuntu to be installed to (win 7 disk manager does not create extended partitions per se). All partitioning operation have to treat the drives as a raid set for the partitioning to be valid. Which is why I asked which release of Ubuntu you are trying to install. The different releases behave differently with 'fakeraid' which is what you are trying to use.

As you see,there is much more involved when you try to use a raid, especially in an environment shared between windows and linux. It is very doable but you need very specific guidance. Much is available in community docs. But I would need to better know what you are working with and where you are to be able to tell you much more.

---

### Post by watchman323 on 2010-11-11
This is what I want to do.  I have  3 physical drives.  One drive is 500gb.  I want win 7 with ubuntu.  Within this 500gb, 200 goes to window 7 and 300gb to ubuntu.  Then I have two identical drives on RAID 1 for data purpose.   When I use live cd, the 500gbgb does not show up at all.  I can only see my RAID 1 drive for partition.

---

### Post by ronparent on 2010-11-11
I do need to know which Ubuntu release you are using. 

The rest is clearer. Win 7 is already installed on the first drive, a 500 gb non raid. You want to install Ubuntu ??.?? on that same drive. Let's ignore the two raid drives for the time being. Delete the two partitions you created on that 1st drive for the install - use the win7 disk utility for that. How many partitions does win7 show remaining?

Start the live cd and verify that the partitions on that 1st drive are visible. If not, it may have been in a raid at one time, The meta data remaining on it may be blocking visibility to the live cd. If so - the meta data has to be erased. To do that, in a terminal (still from the live cd) write: 
> sudo dmraid -E -r /dev/sda
Just make sure that 500 Gb drive is sda (otherwise you will destroy the raid).

At whichever point you can see that drive with win 7 as a separate drive in gparted, use gparted to create a extended but unallocated extended partition in place of the unallocated space.

You are now ready to install. Start the install from the desktop icon in the live session. When you get to the partitioning step elect to manually partition. From the manual partitioning screen elect to first create your swap - it shouldn't require space in excess of you RAM. Elect to create a partition to install Ubuntu next - use up the rest of your unallocated space in the extended partition. You will be presented with a screen to tell the installer what you want to do with that partition. Make sure to check the box to format it, what type partition you want (probably ext4, or ext3, ext2, etc) and a mount point (/) - make sure to select the mount point. The install should now run to finish and a reboot should make you system bootable in either win 7 or Ubuntu. You will probably have to fix you system after install to see the raid drives. That is merely a matter of installing dmraid. If you run into problems, post and I or someone else can help you with it. Good luck.

---

### Post by watchman323 on 2010-11-11
Thanks Ronparent.
When I put the 500gb in "RAID READY" , that prevented live cd 10.10 from being able to see all of my drives.  I don't even know why I put 500gb in "RAID READY".

---

### Post by ronparent on 2010-11-11
You plugged the drive into the same controller you are using for your raid set. Presumably, if you have not configured that drive into a raid set it should not have raid meta data written to it. But if it does, you probably need to make sure that the drive is removed from any raid configuration in the raid bios. Then you should be able to erase the raid meta data if any. Alternatively, you may be able to plug it into a SATA port that is not set as raid. In any event you need to divorce the drive from any raid configuration in bios to get it recognized as a ordinary drive. I have no idea what you MB bios is so I can't at this point be more specific.

---

### Post by watchman323 on 2010-11-12
Ronparent,
I have Asus crosshair formula IV.  I am going to erase my 500.gb harddrive using my bios. Then I am reinstall everything from your instruction.  
Thanks for all of your help.

---

