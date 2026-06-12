---
title: "Using GParted to partition new, replacement harddrive cannot boot"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by rpete on 2010-10-07
Hi, I decided to get rid of my old hard drive and replace it with a new one.  I had a problem upgrading to 10.04 so I thought with a new clean harddrive I could set up 8.04 from the DVD and then upgrade online.  I thought the Ubuntu 8.04 DVD would format the drive and set up a partition but it didn't.  When I ran the command sudo fdisk -l it read sda doesn't contain a valid partition table.  So I used GParted to create a partition using the entire drive.  Now when I run sudo fdisk -l I get /dev/sda1 and everything looks correct: it starts at cylinder 1 and ends at 60801.  There are 60801 cylinders.  It has an ID of 83 and the system is Linux.  But I cannot boot from the internal hard drive.  When I turn on power I hit f12 and arrow down to CD to boot.  

Also, it may be unrelated, at the terminal the prompt is ubuntu@ubuntu:~$  but it should be richard something.  I think I have to set up again the user and password.  

What can I do?

---

### Post by florus on 2010-10-07
Start again. Download or buy a Ubuntu 10.10 CD and take your time installing. Create 3 partitions: root (ext4) 10GB; swap 5 GB; and home (ext4) the rest of the drive.
The figures I have given are only suggestions and can be varied to suit your needs.

---

### Post by e79 on 2010-10-07
This would be my personal suggestions :
 
1. **Make a complete backup of your /home directory**.
2. Download and burn a 10.04.1 LTS cd/dvd
3. Shutdown your PC and replace the hard drive
4. Now boot from the 10.04.1 LTS cd/dvd and start the install again
5. Once the installation is done, copy back your data in your /home folder
 
Seeing that you have ubuntu@ubuntu as username-machinename implies that your are still on the LiveCD/DVD
 
There are several post about issues upgrading from one version to another, this is why I recommend a clean install on the most recent Ubuntu LTS (10.04.1)
 
Just my $0.02

---

### Post by Rubi1200 on 2010-10-07
> ubuntu@ubuntu:~$

This is the prompt you see when running the** LiveCD**.

---

### Post by dabl on 2010-10-07
It looks like you have several possible issues rolled together there -- let's pull them apart.

1. Hard drive preparation:
- In GParted, "Device > New Partition Table (or something like that)", and choose "MS-DOS" as the table type
- In GParted, starting with 100% "unallocated space", right-click on the graphic and "New" to make partitions
- You probably want more than one partition -- you'll need swap if (a) you run out of physical memory, or (b) you want to Suspend to Disk.  Make a swap partition equal to 1.1 X your memory, and you'll have no regrets
- In GParted, right-click and "format" and choose ext4 for the Linux partition(s), and "Linux swap" for the swap partition, if you didn't do that when you made the partition.

2. Installation of the OS
- Why 8.04 -- can you not burn a 10.04 CD?
- Make an "Alternate Install" CD, boot it, and choose "manual partitioning", then just select the partition(s) and mount points.
- Grub installation -- unless you have more complexity than described, just choose "MBR" of the hard drive

3. Boot issues -- this is all about BIOS settings.  Upon starting your computer, go into BIOS and review the "Boot Device" and "Boot Sequence" settings, as applicable, and make sure they reflect what you want to happen.  Typically the "optical drive" or "removable device" is the first/top device, then the first hard drive.  The *buntu CD needs to be removed from the optical drive when you reboot after installation.

---

### Post by rpete on 2010-10-07
Thanks for your responses.   I had removed all data from the old drive and put it on an external drive before I put in the new internal hard drive.  So I don't need to worry about deleting files, thank God.  

I am debating whether to burn a CD with the  10.04 upgrade or work within GParted, but am relieved my options seem like things that are not too difficult for someone like me who is not all that confident with linux.  Thanks, too,  for the suggestion to create several partitions for swapping, etc.  

I will decide what to do and report back on what worked!

---

### Post by rpete on 2010-10-08
Using GParted I have partitioned my new drive into home and left 15GB for two other partitions.  I set the boundaries and I have the options of linux swap or ext2 or ext3 for filesystem.  Home is ext2, should the root be ext2?  Also, am I creating a primary partition or an extended one with the root and swap partitions?

---

### Post by rpete on 2010-10-08
Answered part of my question by reading other threads.  I guess it doesn't matter if root is ext2 or ext3 filesystem, swap must be linux swap filesystem, so that leaves the question of am I creating a primary or extended partition?  From a lay point of view I would think home is the primary and root extended but I don't want to proceed on guessing.  Also is the swap partition primary or extended?

GParted documentation did not clear this up. Some assumptions are made about the level of familiarity using Linux that may need to be reconsidered.  There is nothing like a step by step manual which incorporates all of the options.

---

### Post by e79 on 2010-10-08
I would personally use Ext4 or Ext3 over Ext2 since the latter has no journaling system (in case of crashes it might help) and is more stable IMO.
 
For the partitionning scheme, you can have up to 4 Primary partitions. If you plan to use more than that, you will need an Extended Partition, but up to 4, you can stay with Primary.
 
You can get more infos on EXTx differences here  [https://ext4.wiki.kernel.org/index.php/Frequently_Asked_Questions#What_is_the_difference_between_ext2.2C_ext3.2C_and_ext4.3F](https://ext4.wiki.kernel.org/index.php/Frequently_Asked_Questions#What_is_the_difference_between_ext2.2C_ext3.2C_and_ext4.3F)
 
Hope this helps

---

### Post by srs5694 on 2010-10-08
I would create as many partitions in logical form as possible. The reason is that, as e79 states, you're limited to four primary partitions, but some OSes (such as Windows and FreeBSD) insist on installing to a primary partition. Thus, it's possible you'll need enough primaries to support such OSes that you'll run out of them if you devote Linux space to primaries unnecessarily.

Another option: If you don't plan to install Windows or any very old OS (OS/2, BeOS, DOS, etc.) on the disk, you might want to consider using the [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) partitioning scheme, rather than the standard [Master Boot Record (MBR)](http://en.wikipedia.org/wiki/Master_boot_record) scheme. The reason is that GPT offers a number of minor advantages over MBR, such as elimination of the primary/extended/logical distinctions, redundant data structures for safety, CRCs of data structures to let an OS or utility detect corruption, and labels for partitions. There's also one big advantage that's not yet an issue for most people: GPT can handle larger disks -- MBR tops out at 2 TiB for most drives. (There are ways to fudge this, but it's best to assume a 2 TiB limit.) OTOH, some buggy BIOSes have problems booting from GPT disks. These problems can usually be overcome, but if you prefer not to risk the hassle, sticking with MBR makes sense. Windows also can't boot from GPT disks on BIOS-based computers, so if you want to dual-boot Windows, don't use GPT.

To use GPT, you'll need to create a fresh partition table and select an option to make it a GPT disk. (This option may be buried under an "advanced" setting, depending on the utility you use.) Be sure to create a small (1MiB is more than enough) [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) for GRUB 2's use. (*Do not* attempt to mount this partition in Linux; it's used without a filesystem by GRUB 2.)

---

### Post by florus on 2010-10-08
There is a useful article on disk partitioning <a href="http://en.wikipedia.org/wiki/Disk_partitioning">here</a>

Sorry, I seem to have formatting turned off.

---

### Post by rpete on 2010-10-08
Hi, thanks for the advice.  I don't plan to have a dual OS and 500GB hard drive will be enough so I don't think the GPT partitioning scheme would be good for me.  

Here's what I did so far:  sda1 is 450GB it is intended to be Home, sda2 is 10GB it is intended to be root, sda3 is about 5GB it is linux swap. They are all primary partitions.  I am satisfied with these partitions but I have some remaining issues.  

I am running off the Live 8.04 CD.  In terminal, the prompt is: ubuntu@ubuntu:~$  

1.  How do I get the prompt to be delldesktop, or richard?  I need to mount the partitions, don't I?  How do I do this?  

2.  When I click on places in the toolbar, there is a 450GB media and a 10GBmedia.  These are what I want to be the Home and Root partitions, respectively.  These shouldn't be separate from the Home folder.  How do I change this?  (I think solving question 1 solves 2 or vice versa.)

3.  I want to upgrade to 10.04.  It was suggested I download the image and burn a CD and then install it but how do I do this?  I downloaded the iso to the desktop.  I click on it which opens up the box "Writing to disk".  I click on "write" and then a second box tells me to insert a blank or rewritable DVD. I do so and click Ok but it isn't recognized.  What is going on here?

Your help is much appreciated.

---

### Post by florus on 2010-10-08
If you are running off the live CD, the prompt you have is correct. It is the default prompt, and as you cannot write to the CD, it will not change.
In Gparted, format the 450 GB partition with home as the mount point, and the 10 GB with Root as the mount point. After installing Ubuntu to the hard disk, remove the live CD and reboot. You should then be able to run Ubuntu from your hard disk. 
I would still recommend buying a current version, 10.04 or 10.10, from the Ubuntu shop or a recognised distributor before you do anything else. the improvements since 8.04 are considerable and you will have the latest versions of all the included programs. To my mind there is no advantage in installing an obsolete version and then having to upgrade.

---

### Post by srs5694 on 2010-10-08
> **rpete said:**
> Hi, thanks for the advice.  I don't plan to have a dual OS and 500GB hard drive will be enough so I don't think the GPT partitioning scheme would be good for me.

It's not *necessary,* but IMHO there are still modest advantages in your case, unless you mistyped "don't" when you meant "do."

> Here's what I did so far:  sda1 is 450GB it is intended to be Home, sda2 is 10GB it is intended to be root, sda3 is about 5GB it is linux swap. They are all primary partitions.  I am satisfied with these partitions but I have some remaining issues.

10GB for root (/) is adequate for a small installation, but it could prove limiting if you install lots of software. You're not exactly low on disk space, so you might want to boost that up to 15GB or even 20GB. Also, as described in my earlier post, I'd recommend making one or two of those partitions logical. I'd probably do it like this, given an MBR setup:


[list]
[*]/dev/sda1 - root (/); primary
[*]/dev/sda2 - extended
[*]/dev/sda5 - swap; logical
[*]/dev/sda6 - /home; logical
[/list]


The reason for the ordering and specific primary/logical assignment is that this will let you put GRUB in /dev/sda1, if you so desire. This has some advantages because you can use a standard DOS/Windows boot loader in the MBR, which obviates the need to put GRUB code in the unallocated sectors following the MBR and can make it easier to recover Linux's bootability if you subsequently decide to install Windows. Putting swap space in the middle of the disk minimizes seek time to the swap partition, on average, which can improve performance if you start using swap space. (OTOH, if swap seldom gets used, this will slightly increase seek times between the root (/) and /home partitions.)

> I am running off the Live 8.04 CD.  In terminal, the prompt is: ubuntu@ubuntu:~$  

1.  How do I get the prompt to be delldesktop, or richard?  I need to mount the partitions, don't I?  How do I do this?

This is two entirely unrelated questions.

I wouldn't bother changing the prompt on the live CD or installer. If you want to change it after you've installed the OS, you can edit the $PS1 environment variable. See [here,](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/) among other sources, for information.

As to mounting the partitions, if you're installing Ubuntu, don't worry about it; the installer will do that. If you want to transfer an existing system, there are several ways to do that. The easiest is probably to use a tool like [Clonezilla;](http://clonezilla.org) but it's also possible to do it using tar, cpio, or numerous other tools. Some of these will require you to mount the new partition(s) with a command like "sudo mount /dev/sdb1 /mnt/"; or you can let the GNOME desktop's automounter do the job.

> 2.  When I click on places in the toolbar, there is a 450GB media and a 10GBmedia.  These are what I want to be the Home and Root partitions, respectively.  These shouldn't be separate from the Home folder.  How do I change this?  (I think solving question 1 solves 2 or vice versa.)

You mount one inside the other. For instance:

```

sudo mount /dev/sdb1 /mnt
sudo mkdir /mnt/home
sudo mount /dev/sdb6 /mnt/home

```

If you install directly from a CD/DVD, this will be done automatically.

> 3.  I want to upgrade to 10.04.  It was suggested I download the image and burn a CD and then install it but how do I do this?  I downloaded the iso to the desktop.  I click on it which opens up the box "Writing to disk".  I click on "write" and then a second box tells me to insert a blank or rewritable DVD. I do so and click Ok but it isn't recognized.  What is going on here?

I'm not sure; I'm not all that familiar with the GUI tools, it's not clear to me what GUI tool you're using, and the description of the error is vague. Try this at the command line, after you insert a blank disc, and report the results:

```

growisofs -Z /dev/dvdrw=/path/to/downloaded-image.iso

```

Substitute the correct filename (and path, if necessary) to your image file for /path/to/downloaded-image.iso. It's conceivable you'll need to change /dev/dvdrw, too, but probably not. Note that it really is an equal sign, with no spaces, between /dev/dvdrw and the image filename.

---

### Post by rpete on 2010-10-08
All good advice.  Thanks again.  I will increase the root partition. Although I do not plan on adding Windows, I am aware that extended partitions can contain numerous logical partitions so there is more flexibility than with primary partitions. The swap partition I may put after root and home to improve seek time.   The problem with downloading the desktop image of 10.04 or alternate install CD I will ignore because I decided to buy a CD with 10.04 on it.  Hopefully it will come in the mail in a few days! I'd like my computer to get back to normal!  I forgot about the terminal command sudo (device) mount. I can either do those commands after I get the partitions how I want them, or I can wait until I get the 10.04 CD.

---

### Post by rpete on 2011-01-13
Hi, thanks for the good advice. I waited literally months for the CD with 10.04 on it before finding it for sale and getting it in a few days.  I installed it and created three partitions, root, extended/home, and swap.  Everything is working fine now with a new hard drive and new OS.  GParted was invaluable.

---

