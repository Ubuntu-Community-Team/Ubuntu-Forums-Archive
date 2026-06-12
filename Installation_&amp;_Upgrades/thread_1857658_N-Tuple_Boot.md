---
title: "N-Tuple Boot"
date: 2011-10-10
forum: Installation &amp; Upgrades
---

### Post by Gankro on 2011-10-10
I tried looking around for anything similar to what I'm trying already to little success, so hopefully this isn't a misplaced/duplicate thread or anything.

I've been using Ubuntu (Natty) for about 6 months dual booted with Windows 7. Beyond the typical fights with various drivers, it's been a pretty solid experience. As such, I've grown increasingly interested in exploring the other Ubuntu/Debian derivatives and Linux flavours. I've got a slave Dell with 2 1TB hard drives inside so I figured "hey, why not just partition one of those into a bunch of different distros?"

Right now I've got Windows and 99.9% of my files on one, and Ubuntu on the other. I plan on partitioning the Ubuntu one to test out fully installed out-of-the-box Xubuntu, Kubuntu, Linux Mint, Fedora, and OpenSUSE, giving each one (including Ubuntu) about 150GB. I was wondering what would be the best way to approach this (and am willing to accept "don't" as an answer). Primarily I'd like to know the best way to do this partitioning, as well as the best way for getting the GRUB boot up menu that Ubuntu automatically set up to also acknowledge these others as valid boot options.

I mostly use this computer for browsing and media, and want to test out what kind of out-of-the-box experience they provide without keeping around half a dozen live CDs/USBs or running things virtually or in parallel or something. I also don't really want to have any co-dependencies because I really do want to emphasize how they behave from scratch. If there's a much better way of doing this altogether, I'd love to know!

---

### Post by oldfred on 2011-10-10
Welcome to the forums.

Two issues. Which boot loader and where is data.

You want the boot loader you keep in the MBR and controlling boot to be the one you keep and use most often. Most Ubuntu installs do not give you an option not to install a boot loader, but you can just install to a partition even though it is not recommended and never use it. If your main install uses grub2 you can then just run sudo update-grub and it will find your new install.

I use 20 to 25GB / (root) partitions and keep all data in other partitions. Originally sharing with XP I used NTFS and still have my Firefox & Thunderbird profiles in that shared partition even though not booting XP much. I also have data in another ext3 partition but only share with other Debian based system as the UID & GID is 1000. Others may use 500 or other UIDs and then you can have major issues on sharing ownership and permissions.

Keeping track of what is where, I use labels and still have issues. You need to learn about boot_info script as it documents system. I run It before & after every install to make sure I know what I did. Two of my 4 drives are gpt and I plan on converting sdc to gpt since it will never have Windows. I also created space for an efi partition but that would only be used if I move drive to new system.

```
/dev/sdc1: LABEL="grub" UUID="9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc2: LABEL="Shared" UUID="44332FD360AA9657" TYPE="ntfs" 
/dev/sdc4: LABEL="bios_gpt" UUID="bbda6045-bb8a-4666-8bd4-04b3945ca581" TYPE="ext2" 
/dev/sdc5: LABEL="Karmic" UUID="117412d5-2dbe-4011-8aec-ae310d1ee6c7" TYPE="ext4" 
/dev/sdc6: LABEL="Data" UUID="a55e6335-616f-4b10-9923-e963559f2b05" TYPE="ext3" 
/dev/sdc7: LABEL="LUCID" UUID="5e25282c-9c54-45df-9e79-514011e98648" TYPE="ext4" 
/dev/sdc8: LABEL="Test" UUID="af29c61a-34e9-48eb-9c94-afcb4bb61582" TYPE="ext4" 
/dev/sdc9: LABEL="OLDG" UUID="F6A6-705D" TYPE="vfat" 
/dev/sdc10: LABEL="newhome" UUID="b8a7e331-a716-4ac1-bf58-6ac515606c6d" TYPE="ext4" 
/dev/sdc11: UUID="09367687-86d1-4fd0-9b81-2787d3196159" TYPE="swap" 
/dev/sdc12: LABEL="Puppy" UUID="07e2a08d-37ca-4cf1-877b-f02b0eabcbca" TYPE="ext4" 
/dev/sdc13: LABEL="natty" UUID="318fd41e-4210-4960-a0d9-ee9b48388d69" TYPE="ext4" 
/dev/sdc14: UUID="2b42c9ad-4304-4a8a-8991-08cfe35717ec" TYPE="ext4" 
/dev/sdc15: UUID="2c05178d-1e0e-4ae8-80e6-a700dc0d6eb9" TYPE="swap" 
/dev/sdc16: LABEL="oneiric" UUID="63d146fd-1c63-4b31-95c5-ab52e2892283" TYPE="ext4" 
/dev/sdd1: LABEL="EFI" UUID="7B30-5ACA" TYPE="vfat" 
/dev/sdd3: UUID="09c248c7-1b7f-4b19-9630-a5f945fdccf2" TYPE="ext4" 
/dev/sdd4: UUID="654e22fa-afe6-4503-b89c-cb42c1136482" TYPE="ext4" 

```

---

### Post by Hakunka-Matata on 2011-10-10
Hi, and Welcome to the forums;

You can do that a number of different ways as you already likely realize.  Download the distro.iso files you want to experiment with first, that'll be the most time consoming.  Put them all in a folder, like Downloads/isos or some such.  
If you want to do it the clean way, you then make a custom entry for the grub boot menu, which will list all your different distro's of linux you have.  Boot any one of them as a liveCD straight from your hard drive.  There are several very good threads about it right here on the forums.  [Here's]("http://ubuntuforums.org/showthread.php?t=1838959") one.
**EDIT: **oldfred is where I learned to do it myself, so you've found good advice already.

---

### Post by Gankro on 2011-10-10
> **oldfred said:**
> Welcome to the forums.

Two issues. Which boot loader and where is data.

You want the boot loader you keep in the MBR and controlling boot to be the one you keep and use most often. Most Ubuntu installs do not give you an option not to install a boot loader, but you can just install to a partition even though it is not recommended and never use it. If your main install uses grub2 you can then just run **sudo update-grub** and it will find your new install.

I use 20 to 25GB / (root) partitions and keep all data in other partitions. Originally sharing with XP I used NTFS and still have my Firefox & Thunderbird profiles in that shared partition even though not booting XP much. I also have data in another ext3 partition but only share with other Debian based system as the UID & GID is 1000. Others may use 500 or other UIDs and then you can have major issues on sharing ownership and permissions.

Keeping track of what is where, I use labels and still have issues. You need to learn about boot_info script as it documents system. I run It before & after every install to make sure I know what I did. Two of my 4 drives are gpt and I plan on converting sdc to gpt since it will never have Windows. I also created space for an efi partition but that would only be used if I move drive to new system.

```
/dev/sdc1: LABEL="grub" UUID="9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc2: LABEL="Shared" UUID="44332FD360AA9657" TYPE="ntfs" 
/dev/sdc4: LABEL="bios_gpt" UUID="bbda6045-bb8a-4666-8bd4-04b3945ca581" TYPE="ext2" 
/dev/sdc5: LABEL="Karmic" UUID="117412d5-2dbe-4011-8aec-ae310d1ee6c7" TYPE="ext4" 
/dev/sdc6: LABEL="Data" UUID="a55e6335-616f-4b10-9923-e963559f2b05" TYPE="ext3" 
/dev/sdc7: LABEL="LUCID" UUID="5e25282c-9c54-45df-9e79-514011e98648" TYPE="ext4" 
/dev/sdc8: LABEL="Test" UUID="af29c61a-34e9-48eb-9c94-afcb4bb61582" TYPE="ext4" 
/dev/sdc9: LABEL="OLDG" UUID="F6A6-705D" TYPE="vfat" 
/dev/sdc10: LABEL="newhome" UUID="b8a7e331-a716-4ac1-bf58-6ac515606c6d" TYPE="ext4" 
/dev/sdc11: UUID="09367687-86d1-4fd0-9b81-2787d3196159" TYPE="swap" 
/dev/sdc12: LABEL="Puppy" UUID="07e2a08d-37ca-4cf1-877b-f02b0eabcbca" TYPE="ext4" 
/dev/sdc13: LABEL="natty" UUID="318fd41e-4210-4960-a0d9-ee9b48388d69" TYPE="ext4" 
/dev/sdc14: UUID="2b42c9ad-4304-4a8a-8991-08cfe35717ec" TYPE="ext4" 
/dev/sdc15: UUID="2c05178d-1e0e-4ae8-80e6-a700dc0d6eb9" TYPE="swap" 
/dev/sdc16: LABEL="oneiric" UUID="63d146fd-1c63-4b31-95c5-ab52e2892283" TYPE="ext4" 
/dev/sdd1: LABEL="EFI" UUID="7B30-5ACA" TYPE="vfat" 
/dev/sdd3: UUID="09c248c7-1b7f-4b19-9630-a5f945fdccf2" TYPE="ext4" 
/dev/sdd4: UUID="654e22fa-afe6-4503-b89c-cb42c1136482" TYPE="ext4" 

```

Ah! Telling me about update-grub (I definitely have GRUB 2) was a huge help! I got Xubuntu running already on its own root partition.  I'll definitely make sure to also look into boot_info. 

So if my windows partition is on sda, and all my linux distros are on sdb, how will those distros expect things to work? Will they all want to install their own programs onto their own partitions, or will they realize there are other distros/partitions and try to do something "smart"? How would I *encourage* them to be "smart" if I wanted them to be? For instance if I wanted them to all run the same copy of firefox, share the same home directory, or install all programs to the same partition, how would I go about doing this? Is this easier to do during the initial install/partitioning process, or is this something I strictly need to do afterwards? Is what I pick partitions to be (root, home, etc...) relevant to this?

Sorry for all the questions, I'm afraid that even though I am a programmer, I don't know a lot about low level stuff like operating systems, boot configurations, and hard drive partitioning.

---

### Post by oldfred on 2011-10-10
You can share data, but not really anything else. we suggest a separate /home so you have your data & user settings separtate from system but that is only for ease of upgrades. Programs are made to upgrade settings but not really downgrade.

With many different versions of programs, desktop environments you will not have any consistency. 

This is all you can share but even this can have issues. NTFS partition will not have sharing issues as it has no ownship nor permissions.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by Gankro on 2011-10-11
Ah, okay (so many options!). Just to clarify, in your personal setup (which is sounding attractive) all your distros have their own fairly small /home directories with all the user settings and what not, and then they also link/bind/share some separate /Data directory which sits in its own partition for all your documents/media? Making /Data NTFS would also mean Windows would be able to see and interact with it natively right? Would that slow down Ext4 partitions interacting with it in any substantial way?

I assume that if I try to share more than just documents/media, even if I'm using only Debian based systems, they'd likely begin to wreak havoc with each other's programs/settings, right? And if I did use non-Debian ones, then it'd be especially nightmarish?

And of course if I ever change my mind about certain partitioning things I can usually repartition (within reason) to suit my needs from a Live CD anyway, right?

---

### Post by oldfred on 2011-10-11
An advantage of Linux is the options, but for a new user it is a disadvantage when first starting.:)

I originally changed to a separate /home and often suggest that to new users so they can easily do new reinstalls without losing data & settings. But I had started sharing with XP and had some data there. I now have so little data (1GB) in /home I just keep it in the / (root) partition. 

Then with most data I now have it in a ext3 partition that I share with several Ubuntu installs. I keep most older and newer installs all as active and bootable and every one mounts both my ext3 /mnt/data and my /mnt/shared partitions and link folders from those partitions into /home.

I found I was running the same set of commands to mount & link my data & shared partitions that I listed history (all the commands you have run in terminal) and just copied them to a bash file. I had to tweak a few things but that auto mounts, edits fstab and links all my folders into /home for every new install.

---

