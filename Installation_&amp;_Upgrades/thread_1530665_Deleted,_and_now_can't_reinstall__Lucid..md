---
title: "Deleted, and now can't reinstall  Lucid."
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by amir_zwara on 2010-07-13
I deleted Ubuntu off of my laptop, because I was having some issues with it (I had lost some of my icons in Software Center, couldn't access my Yahoo Mail etc..). I deleted it using this [http://ubuntuforums.org/showthread.php?t=113630]("http://ubuntuforums.org/showthread.php?t=113630") method. I then went into my Windows Vista OS, and accessed Disk management via Control Panel.
The partition Linux was previously on was Unallocated, and I had a D partition which was Windows recovery. I then shrunk my C (main Windows) partition down. I deleted the D partition.So now I have the C partition, and a large unallocated partition. I was planning on installing Ubuntu from CD onto this unallocated partition. I am using the same CD I had previously used to install Ubuntu. My roommate was also using the same CD today to install Ubuntu on his computer. I know the CD works.
So when I inserted the Ubuntu CD it loaded the first couple of screens. It got to the purple screen where the install text would normally have appeared and then continues to load.... but the "do you want to install? etc..." text did not come up. It then loaded to a black screen, loaded back to the purple screen, reads the disc, keeps loading... and loading... and nothing ever comes of it.
I tried again, this time when the first purple screen comes up, I hit enter. I get the language select. I then get the options. I click install Ubuntu. it then starts loading... and loading... black screen, purple screen, black screen with text... but nothing comes of it.
My windows is working fine. I don't know why it won't install...
Any suggestions?

---

### Post by rolleander on 2010-07-13
Try installing using non-graphical method and manually setting up the partitions. Reformat the unallocated partition only (don't touch the win partition of course!) and also be sure that the filesytem is ext4 and set to bootable

I had a similar problem doing a reinstallation of Debian 5.0 on a machine a while ago

---

### Post by rolleander on 2010-07-13
Oh and while I'm still thinking about it - don't forget to add a swap partition...

---

### Post by amir_zwara on 2010-07-14
How do I do a manual install and partition?

---

### Post by alterpinguin on 2010-07-14
manually create harddiskpartions...
-
Boot the INstall-CD into the live-Version,
(you may need to press Up/Down key to activate the boot-menu of the install-CD, then select your options... )
-
after the Live-System is running,
check your system, hardware-settings, name of harddisk, partitions.

I still use the old fdisk program, but you may use a newer gui-version.
You have to be root to run such programs like fdisk.
Start a terminal and enter there:
sudo su
then, i assume your harddisk is /dev/sda (the first one sdb is second ..)
enter:
fdisk /dev/sda
-
!! if you never used partition-tools like this, you should read about it and not type what i show as an example,
p - shows the partition table of the harddisk
n - adds a new partion, you need to specify start, end and type (linux)
q - quits without changes
w - writes the partition table to the disk -- DANGER!
-
After this, you can format this new partition with an linux-format,
reiserfs, ext3, ..
-
There is a system-limitation:
you can only have max. 4 primary partions on one harddisk
you can only have 1 extended partition on one harddisk
and in an extended partition you can create more than 4 "l"ogical partitions, so if you need a separate swap-partition and one root-partition and maybe a separate home-partition, it is necessary to have a big extended partition where to setup those partitions as logical partitions.

---

### Post by amir_zwara on 2010-07-14
> **alterpinguin said:**
> manually create harddiskpartions...
-
Boot the INstall-CD into the live-Version,
(you may need to press Up/Down key to activate the boot-menu of the install-CD, then select your options... )
-
after the Live-System is running,
check your system, hardware-settings, name of harddisk, partitions.

I still use the old fdisk program, but you may use a newer gui-version.
You have to be root to run such programs like fdisk.
Start a terminal and enter there:
sudo su
then, i assume your harddisk is /dev/sda (the first one sdb is second ..)
enter:
fdisk /dev/sda
-
!! if you never used partition-tools like this, you should read about it and not type what i show as an example,
p - shows the partition table of the harddisk
n - adds a new partion, you need to specify start, end and type (linux)
q - quits without changes
w - writes the partition table to the disk -- DANGER!
-
After this, you can format this new partition with an linux-format,
reiserfs, ext3, ..
-
There is a system-limitation:
you can only have max. 4 primary partions on one harddisk
you can only have 1 extended partition on one harddisk
and in an extended partition you can create more than 4 "l"ogical partitions, so if you need a separate swap-partition and one root-partition and maybe a separate home-partition, it is necessary to have a big extended partition where to setup those partitions as logical partitions.

Ok, so you're saying: load the Ubuntu install CD, and do the run from CD option?
Once in, check my hardware, system, partitions, etc... then create a new linux partition, in Terminal, using the above coding?
something like whats on this site?
[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html]("http://tldp.org/HOWTO/Partition/fdisk_partitioning.html")

So what partitions do I want/need?
Like I said, I have now One windows partition, and one big unallocated partition. So I will make the unallocated into one "extended partition," that will have a swap/other logical partitions within it? And what else? Do I want/need a home partition? what about a root partition?
Sorry, this is all new to me, but I am very interested in learning to do this, and moving forward in the Linux world.
Thanks.

---

