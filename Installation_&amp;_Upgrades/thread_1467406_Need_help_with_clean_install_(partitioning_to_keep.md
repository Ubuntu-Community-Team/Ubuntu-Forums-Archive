---
title: "Need help with clean install (partitioning to keep my files)"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by user333 on 2010-04-30
Hi :) I need a little advice on how to upgrade my ubuntu 9.10 system. I would like to do a clean install of lucid, but I have way too many files. I have a big hard drive, so space was not a problem, and things got out of hand ^^ One thing you should know is that I have plenty of room for my files even if the drive was half it's size, so my idea is possible space-wise. (And I am prepared if this fails. I have backed up my stuff, but would like if it I didn't have to rely on that)

What I want to do is make a blank partition with gparted and install lucid on it. Then I want to keep it a dual boot just to make sure my hardware is working ok, then move my home folder to the new partition, make the lucid partition take the whole hard drive, and delete karmic. I do not want to upgrade because I messed up my install a lot while learning linux, so I really need to start over. Could anyone tell me if this is possible?

thanks

---

### Post by user333 on 2010-04-30
does anyone know???

---

### Post by user333 on 2010-05-01
ok... It worked
never mind about it

---

### Post by oldfred on 2010-05-01
Ok, a day late & a dollar short.

I have 3 Ubuntu partitions current install, previous install and beta where I only test new versions. I plan on alternating previous & current so I always have a second way to boot on the hard drive.

When I upgraded to Karmic I moved /home to a new 100GB partition. My current root is now only 5GB with lots of programs installed. So I recommend that you only need 10-20GB for root partitions. I then moved all my data out of /home so home only has system settings and some misc data. Now my /home is 1GB (still in that 100GB partition) and all my data is in a /data partition. I can easily mount /data in any system as that has no system settings (as I am thinking of testing other systems). Separate /home is just for Ubuntu and for the current version(as new installs are added).

---

### Post by RedRat on 2010-05-01
> **oldfred said:**
> Ok, a day late & a dollar short.

I have 3 Ubuntu partitions current install, previous install and beta where I only test new versions. I plan on alternating previous & current so I always have a second way to boot on the hard drive.

When I upgraded to Karmic I moved /home to a new 100GB partition. My current root is now only 5GB with lots of programs installed. So I recommend that you only need 10-20GB for root partitions. I then moved all my data out of /home so home only has system settings and some misc data. Now my /home is 1GB (still in that 100GB partition) and all my data is in a /data partition. I can easily mount /data in any system as that has no system settings (as I am thinking of testing other systems). Separate /home is just for Ubuntu and for the current version(as new installs are added).
Hmm. I kinda like what I read here. As you can tell, I am a newbie at this although I have been using Ubuntu for about 3 years. The partitioning thing has always seemed a bit mysterious to me so I need to be pointed to some documentation that might clear this up. 

I currently have Hardy installed but have moved all my documents (data) off to a usb drive (it has an ntfs format just in case I need Windows to access it). Before partitioning is it necessary to defragment the disk? The reason I ask this is that I have at one point nearly filled the hard drive and have been using it pretty relentlessly for the past 2 years, so I would imagine some files are scattered around the disk. I know that Linux is not as susceptible to fragmentation as Windows, but it seems to me you want to move all your files together during the partitioning. Again, a pointer would help here.

---

### Post by oldfred on 2010-05-01
If you are creating new partitions, you specify format and it will erase everything. If reusing an existing /home you do not want to format. If shrinking a windows partition it is better to defrag twice before shrinking. IF XP you can use gparted to shrink, but with Vista & 7 it is better to use its MMC to shrink and reboot in windows to make sure it is ok with new smaller size before adding/moving parititons around.

RedRat - you should start your own thread if you have more questions as this is solved and not too many will look at it to contribute more, but just to look at it for solutions.

---

### Post by danielhs on 2010-05-03
> **oldfred said:**
> Ok, a day late & a dollar short.

I have 3 Ubuntu partitions current install, previous install and beta where I only test new versions. I plan on alternating previous & current so I always have a second way to boot on the hard drive.

When I upgraded to Karmic I moved /home to a new 100GB partition. My current root is now only 5GB with lots of programs installed. So I recommend that you only need 10-20GB for root partitions. I then moved all my data out of /home so home only has system settings and some misc data. Now my /home is 1GB (still in that 100GB partition) and all my data is in a /data partition. I can easily mount /data in any system as that has no system settings (as I am thinking of testing other systems). Separate /home is just for Ubuntu and for the current version(as new installs are added).
Fred,

How do you maintain the 3 different partitions?  I'd love to have a setup like that.

I have LVM setup right now, with /home and / (root) as logical volumes with Karmic.

I really want to create a new root for Lucid, but I don't know how to create a new LVM partition *and* have GRUB realize that there are 2 root partitions and either of them can boot.

I was thinking about trying to copy my current root partition (duplicating it) and then starting up the duplicate and running the regular inplace upgrade.  Ie upgrade a duplicate of my Karmic install to Lucid.
But, again, I don't know how to get GRUB to recognize a new partition, even if I copied that LVM partition.

Help would be much appreciated!  Thanks very much.

---

### Post by oldfred on 2010-05-03
I do not know about LVM but are not partitions still partitions? I have 3 partitions and a couple of empty ones for future use. You just install to that partition using manual install. Since I am upgrading I think I have no problems using the same /home as long as I do not plan on using the older version that may have software that does not understand settings written by the newer version.

The last install of grub2 ends up in control and a sudo update grub finds the other installs. I have 3 drives so I do have different versions of grub in each MBR (more for backup) and I customized my menu  with 40_custom as list was getting too long.

---

