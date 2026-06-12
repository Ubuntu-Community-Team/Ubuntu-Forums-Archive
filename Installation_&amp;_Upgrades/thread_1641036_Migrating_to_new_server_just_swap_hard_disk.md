---
title: "Migrating to new server just swap hard disk?"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by TC!! on 2010-12-08
I've edited my original question because I've now made a major decision on how I'm going to migrate from my current Dell SC 440 running 10.10 Desktop over to a HP Proliant Microserver.

I had originally asked if I could just put in the hard disk from one machine to the other but now I've decided to install the server edition of Ubuntu on the HP. I've decided to do it this way as for the last week I've been running Azureus without a GUI and the difference in speed is amazing, so I'm going to run the whole thing without a desktop. It's normally running as a headless machine serving an Acer XBMC and a few Macs.

What I still need to know is what't the best way to move my current setup across?

I'll have a 160GB hard disk in the HP but I want to use my 1TB and 2TB Western Digital Green hard disks from the Dell as they will use even less power.
What I would like to do is start setting up all the features I need on the new machine on the 160GB hard disk first:
SVN
MySQL
Motion
Azureus

What is the best way for me to then migrate this setup from the 160GB disk over onto the 1TB disk without destroying all the home folders I already have?
I already use a separate partition for /home on the 1TB disk so it looks like that will be quite easy, but what would be the best way to transfer the system over, can I just do something like sudo cp -rp ?
What will I need to look out for when it comes to setting up mounts as well?

Any help with this is greatly appreciated.

---

### Post by TC!! on 2011-01-07
I never got a reply but I'm almost finished on sorting this out myself so I thought I'd post here how I did it and ask for help in solving the last piece of the puzzle.

I've now managed to move my 1TB and 2TB western digital hard disks into the new HP server but it's still running / (root) from the original 160GB hard disk. I am using the /home from my 1TB disk and accessing all my media on the 2TB disk.

So this is what I have right now in terms of partitions:
160GB Hard Disk:
/ - used as the main system root
swap - used as main system swap
/home - not used at all now

1TB disk
/ - root from old system - not used
swap - swap from old system - not used
/home - home from old system which is now being used by new system

2TB disk
1 big partition just for media

So what I want to know now is how I get the root from my 160GB hard disk over to the 1TB disk and tell my system to boot from it? I guess the swap will be just editing the fstab to point at the right one.

Finally my only other issue is that the /home on my 1TB drive is still ext3 but everything else is ext4, what's the best way to convert it?

---

### Post by TC!! on 2011-01-07
I promised I'd explain how I got this far in case it helps someone else so here goes.

The main thing which made it easy for me to perform this was that on both my installations I kept my /home on a separate partition. If you don't have this then there's not much point trying to follow what I did.

My main aim was to get the services and users I needed on the new system. I installed everything I needed and made sure it ran OK using the new temporary /home. For some parts of this I needed to create the users I needed.

Because I wanted to just swap straight over to my old /home I had to make sure all the new users and groups matched on both systems. To do this I looked in these two files:
/etc/passwd - users and their ids
/etc/groups - groups and their gids and the users belonging in each group

To force the users I created on the new system to match the old one I used this command:
usermod -u 1000 myuser

So the number after u is the userid you want myuser to be changed into. To force groups to change use this command:
groupmod -g 1000 mygroup

Using these commands along with adduser for creating new users and adding them to existing groups I got both systems with all the users and groups I needed having matching IDs.

Before I moved the hard disks over from my old machine I needed the UUIDs of each partition to be able to set them up in the fstab of the new machine. You can find the UUIDs using this command:
sudo blkid

The output is quite cryptic but if you look at the /dev names and compare them to the output from 'cat /etc/fstab' you can work out which UUID is for your /home for example.

Armed with the UUIDs I needed I moved the hard disks over to the new machine and just rebooted normally at first. I ran the same 'sudo blkid' again just to make sure the UUIDs where correct in the new machine. After I saw they where I then edited the /etc/fstab on the new machine to swap the UUID for /home to use the old hard disk. (one complication for me I also had to change the line from ext4 to ext3 as that's the format of the old /home).

I then rebooted and everything came up working the first time. So that's where I'm at right now. I'd really like to get rid of the 160GB disk as it's just hogging space for future hard disks to be added.

---

### Post by TC!! on 2011-01-25
Any chance of some help with this?

I think I've found out what I need to copy the current root partition from my 160GB disk over to my 1TB drive.
This is the command to clone a partition:
sudo dd if=/dev/sda1 of=/dev/sdb1

Now I just want to know how I mount the partition on my 1TB drive and if that command will take care of changing the partition over to ext4.

This is what I get when I run df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  1.9G   16G  11% /
none                  432M  208K  431M   1% /dev
none                  436M     0  436M   0% /dev/shm
none                  436M  736K  435M   1% /var/run
none                  436M     0  436M   0% /var/lock
none                  436M     0  436M   0% /lib/init/rw
/dev/sdc1             1.8T  1.1T  675G  62% /media/jamie
/dev/sdb2             902G  866G  8.6G 100% /home

And this is the output from sudo blkid:
/dev/sda1: UUID="cbe37e56-94fe-4038-82b3-f791186f3381" TYPE="ext4" 
/dev/sda5: UUID="3da34866-7350-4dde-86cd-4f764a48bdc9" TYPE="swap" 
/dev/sda6: UUID="49a02346-cdad-4e8b-b4b2-824e8e9c4668" TYPE="ext4" 
/dev/sdb1: UUID="f215799e-62af-48b4-bdab-5e97cf7782b9" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb2: UUID="5b03d9d1-f2c6-42e1-8b2c-85f31cc2e408" TYPE="ext3" 
/dev/sdb5: UUID="d51ccdaa-37af-4c5e-a7a7-345a5244ce00" TYPE="swap" 
/dev/sdc1: LABEL="New Volume" UUID="6fc18061-0a5c-4c59-811f-57d9105aa687" TYPE="ext4"

So it looks like I have sda is my 160GB drive I want to replace, sdb is my 1TB drive which has my /home and sdc is my 2TB drive holding my media.

So, my current root is on /dev/sda1 and I want to duplicate it onto /dev/sdb1.
How do I mount sdb1 to be able to do this and will it take care of the ext4 change?

sdb5 will become my swap drive, is it just a case of changing the swap in /etc/fstab?

---

### Post by psusi on 2011-01-25
First, Azerus sucks big time, as do most things written in Java.  Try transmission.

As for moving your root fs, it is no different than moving /home.  Boot from the livecd, mount both disks, and cp -a the files over.  After that you just need to reinstall grub on the new disk to make it bootable, with something like:

sudo grub-install --root-directory=/mnt /dev/sda

---

