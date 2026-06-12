---
title: "Trouble making a 1.9TB (TerraByte) partition in Feisty"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by John_W on 2007-05-18
I'm using a LSI MegaRaid 4-port SATA RAID-5 hardware controller with four 750MB SATA drives which gives approximately 2TB (terrabytes) total size.
When installing Ubuntu 7.04, I'm having problems when it comes to partitioning the drives.
I have searched the forums and found [[COLOR="Red"]THIS POST[/COLOR]]("http://ubuntuforums.org/showthread.php?t=429986&highlight=large+partition") about problems with very large partitions.
Here is what I have found so far...

When I get to the partitioning section of the installation, I get the message that I have to define at least a root ( / ) and swap partitions.
I can make the root ( / ) EXT3 partition 7GB and the swap EXT3 partition 500MB **no problems**.
When I try to make a home ( /home ) EXT3 partition of approximately 1.8TB (terrabytes) I get a size very much smaller than the size I entered or I get the error "end can not be before the beginning" or "the beginning can not be before the end" or words to that effect.

Is this still a bug in Feisty 7.04?

What options are available to make a partition this size?
Will GParted LiveCD be an option. Do I use GParted LiveCD BEFORE I install Ubuntu?

Options and opinions appreciated!

---

### Post by kidders on 2007-05-20
Hi there,

I find the Ubuntu installer quite weak when you try to do anything that deviates even *slightly* from the default configuration. I've seen threads in the past that suggest that, at one point, the installer used to crap out if you tried to use filesystems other than Ext2/3 on partitions!

To be perfectly honest, I almost always do the following, when installing Ubuntu...[LIST]
[*]Use Gparted as little as humanly possible.
[*]Stick with tools like **cfdisk**, **mdadm** and **mkfs** (that I *know* won't screw up) to create partitions & filesystems.
[*]Manually revise partitioning schemes, etc. after installation if necessary.[/LIST]
Generally speaking, Linux doesn't have the slightest problem with large filesystems, so you needn't worry ... once you can dispense with the grumpy installer, everything should work fine. :-)

**Edit:**

Since your problem seems to be with your /home partition, I would suggest not allocating one at install time, and setting it up manually afterwards. (Irritating, but probably just easier!)

[SIZE=1][COLOR=Silver][*[UAResolved]*]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR][/SIZE]

---

### Post by John_W on 2007-05-20
Thanks for the reply!
I'll give your suggestions a try tomorrow and see what happens.
If I'm successful, I will post back so others know what I did to accomplish this.

---

### Post by John_W on 2007-05-29
**Update - FIXED!!**

***Disclaimer***: While I am by no means a LINUX guru, I'm providing this information to help others that may have similar problems. I started this project with bare hard drives and had no data to lose. If you are attempting this on a system that has important data, **PLEASE** backup your data before you start.

Let's see if I can remember the process I used to fix the problem so others can learn from my experience.
Thanks to kidders for setting me on the correct path.

Note: I'm running a LSI Logic SATA 150-4 RAID Card with four 750MB drives attached. Ubuntu works with this RAID card right out of the box! This yields approximately 2250MB (2.25TerraBytes) of disk space. The RAID card apparently limits the logical drive size to 2TB. This gives me two logical drives of size 2097150MB (/dev/sda) and 49050MB (/dev/sdb).
I setup the RAID card and disk drives using this web site as a guide. 
[http://www.smallnetbuilder.com/content/view/27840/77/](http://www.smallnetbuilder.com/content/view/27840/77/) 


1. Ran the Ubuntu 7.04 Live-CD
2. Went through the typical prompts up to the live-CD Desktop
3. From the Live-CD Desktop, started the installation of Ubuntu 7.04.
4. Followed the basic installation prompts up to the point where the drive is partitioned. 
5. Using the guided partitioning of Ubuntu, I'm prompted that I need at least a Root ( / ) and SWAP partitions. I define the Root ( / ) partition on /dev/sda as 20GB and the SWAP partition on /dev/sdb as 1GB. 
That leaves approximately 1.9TB free on /dev/sda and 47GB on /dev/sdb. I will partition these later. 
Note: Tryinig to partition the 1.9TB at this point using the Ubuntu supplied partition utility does NOT appear to work properly. This is where my original problems started. Leave this large empty disk space as is for now.
6. Click forward and allow Ubuntu to continue the installation process following the typical installation prompts.
7. I allow Ubuntu to reboot after installation to make sure the operating system installed properly.
8. After I make sure the installation was successful, I restart the computer again and at the GRUB prompt I hit the "Esc" key to bring up the GRUB options. I select the "Recovery Mode" and allow the computer to come up to a command prompt. (after entering the "root" password)
9. I type cfdisk /dev/sda and selected the empty 1.9TB space and created a new/primary partition with the remaining 1.9TB. When done I write the partition table using the menu at the bottom of the screen. This made the new partition /dev/sda2. Quit cfdisk when done. I left the remaining 47GB on /dev/sdb free for now. 
10. Now I had to make an ext3 file system for the new /dev/sda2 partition.  [COLOR="Red"]See my notes below on changing to the XFS filesystem[/COLOR]
I used this Ubuntu tutorial as a guide.
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018) 
To make the file system I typed the command mkfs.ext3 -L mydata /dev/sda2 
You will have to change the partition specification (/dev/sda2 in my case) to fit your instance. Since my partition is large (1.9TB) it takes a long time to make the file system. It is similar to formatting a drive under DOS or Windows.
11. After the file system is finished I typed reboot at the prompt.
12. After the system reboots back to the ubuntu desktop, I used the terminal to make a directory where the new partition will be mounted. In this case /mydata 
13. I used the nano editor to edit the /etc/fstab to define the mount point. 
Use the links at the end of this post as a guide and the "man pages" for additional help.
Here is what my fstab looks like - Yours will be different. 

fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda2
/dev/sda2 /mydata ext3 defaults 0 1  [COLOR="Red"]See my notes below on changing the filesystem to type XFS[/COLOR]
# /dev/sdb1
UUID=dc7c9d47-4dd0-49ac-a8e0-877f8b35d7c5 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0 

After restarting the computer and making sure that the 1.9TB partition /dev/sda2 was mounted on /mydata I started setting up SAMBA for sharing the Ubuntu computer with Windows computers on the network. 
You will find an excellent Ubuntu Forums article on  "HOWTO: Setup Samba peer-to-peer with Windows" located here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) 

I hope this post will help someone with a similar problem partitioning LARGE partitions.
As a closing note, I also tried to partition the 1.9TB disk space using "GParted Live-CD". That also was a failure. Using cfdisk like I have shown above worked like a charm in my case.
Remember to also see the links below for additional information.

**Important Links**:
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) 

Mount Partitions Automatically
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) 

HOWTO: Setup Samba peer-to-peer with Windows
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)


===========================================================

**COMMENTS FROM FORUM USER: kidders**
After the installation, I would suggest booting from a CD, or another Linux installation, if one is available. 
The point would be to avoid writing to a partition table that contains mounted filesystems, which can be dangerous...

    * 7. Allow Ubuntu to reboot after installation to make sure the operating system installed properly. Then, reboot again.[COLOR="Red"] [This step can be skipped, if you feel comfortable.][/COLOR]
    * 8. Interrupt the boot process & [COLOR="Red"]use a LiveCD instead[/COLOR].
    * 9. I type cfdisk /dev/sda and selected the empty 1.9TB space and created a new/primary partition with the remaining 1.9TB. When done I write the partition table using the menu at the bottom of the screen.
           This made the new partition /dev/sda2. Quit cfdisk when done. I left the remaining 47GB on /dev/sdb free for now.
    * 10. mkfs.ext3 -L mydata /dev/sda2


This is where things start to go a bit funny.

    * (Step 10) Ext3 is probably a bad choice for a filesystem of this size (~2TiB). 
[COLOR="Red"]**NOTE:** I have since changed the 2TiB partition to the XFS filesystem.  mkfs.xfs -L mydata /dev/sda2[/COLOR] I also edited this line on my fstab [COLOR="Red"]/dev/sda2 /mydata xfs defaults 0 1[/COLOR]
    * (Step 11) Rebooting here is not required. (If your system suggests it, you've just done something unwise.)
    * (Step 12) This step can be done immediately after formatting the filesystem.

---

Essentially, creating a new filesystem can be done without ever rebooting, or with a single reboot if you want to modify a partition table containing filesystems you can't dismount ...

   1. cfdisk
   2. mkfs
   3. nano -w /etc/fstab
   4. mkdir


At that point, you can either type sudo mount -a (to avoid rebooting altogether), or sudo shutdown -r now (if you had to use a LiveCD).

If the filesystem being created is large, or is sitting on a RAID array, two additional things become relevant ...

   1. For striped RAID, aligning the filesystem blocks to the stripe size is vital, to avoid ending up with Microsoft-like performance hehe. Some filesystems (including Ext3) provide special options for doing this.
   2. For big filesystems (ie anything over half a GiB), many of the strengths of Ext3 start becoming drawbacks...
          * Its periodic self checks become quite slow.
          * Its "all-purpose" design starts to become a performance drag.
          * Its ability to manage things like fragmentation & corruption (although still excellent) doesn't necessarily scale as well as that of other filesystems.
          * Depending on what the filesystem is being used for, Ext3's use of free space can become extremely inefficient.


On smaller partitions, the distinctions between the various filesystem types are largely academic. In my opinion though, it's worth considering the use of XFS or JFS (or perhaps even ReiserFS), once things start to scale up to a point where tangible gains can be made (or lost!).

===========================================================

Thanks kidders for your kind and encouraging messages!

---

