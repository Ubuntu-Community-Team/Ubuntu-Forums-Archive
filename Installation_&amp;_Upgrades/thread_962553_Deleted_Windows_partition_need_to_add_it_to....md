---
title: "Deleted Windows partition need to add it to..."
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by OBCENEIKON on 2008-10-29
So I have been dual booting Ubuntu with Windows XP for some time now. I deleted my windows partition and want to devote that space to linux.
There is a screenshot of my partition table attached
/dev/sda1 was my windows partition
/dev/sda5 is my root partition
/dev/sda6 is my home partition

I was wanting to add the windows partition to my home partition...maybe a little to my root partition...I just backed up all my files in my home and root partition using cp -a...is this a good method? also should I just reinstall? if I reinstall, can I copy my root and home partition to the new install and just make the changes to my /etc/fstab to reflect the new mount points?

---

### Post by kshane on 2008-10-29
Just delete the old Windows partition and then expand your "/" Linux partition.

---

### Post by fendres on 2008-10-29
> **O[*]Delete sda1 and sda3
BCENEIKON said:**
> So I have been dual booting Ubuntu with Windows XP for some time now. I deleted my windows partition and want to devote that space to linux.
There is a screenshot of my partition table attached
/dev/sda1 was my windows partition
/dev/sda5 is my root partition
/dev/sda6 is my home partition

I was wanting to add the windows partition to my home partition...maybe a little to my root partition...I just backed up all my files in my home and root partition using cp -a...is this a good method? also should I just reinstall? if I reinstall, can I copy my root and home partition to the new install and just make the changes to my /etc/fstab to reflect the new mount points?

Hi,
I think this is tricky, because I don't know if resizing the extended partition works, and if so you would still be unable to use the freed space for your home (where it is probably needed).


The easiest option: Mount /dev/sda1 as a subdirectory in your home

The second easy option would be a fresh install into a new root partition at /dev/sda1 (adapt the size, 10-15GB should be fine) a new swap (do you need 6GB?). If that worked out, delete /dev/sda5 (possibly after merging configuration data), then resize the extended partition and grow /dev/sda6 to take up all of it. 
However, copying the whole old system over the new is not just about /etc/fstab but at least also about files in /boot/grub (the bootloader needs to know the new location of the system too). But you can try that without harm as long as you keep the old root partition.

The not so easy option would be to keep your old system but move around the partitions, so that you have a contiguous home partition.

You did cp -a of what data? I use rdiff-backup (i.e the gui "keep") for the incremental feature.

P.S: Do you really need 6GB swap space? Try "free -m" in a terminal to see swap usage in Megabytes

---

### Post by OBCENEIKON on 2008-10-29
I am liking your second option. About the 6gb of swap, I read somewhere to set your swap as double the amount of memory you had, and since my laptop has 3gb, I put 6gb of swap...what do you recommend?

Here's what free rm shows me.
             total       used       free     shared    buffers     cached
Mem:       3622328    2772188     850140          0      86808    1817556
-/+ buffers/cache:     867824    2754504
Swap:      6996296          0    6996296


As for the cp -a, I ran cp -a /home/* and cp -a / to my external hd
I'll take a look at rdiff-backup.

---

### Post by fendres on 2008-10-30
The doubling rule for swap comes from the era of less than 512MB RAM. I do not know any new rule of thumb but it seems unnecessary to me to have that much for normal usage. According to your post (btw it is "free -m" not "free rm") on your system the swap is not used: 
Swap: 6996296 (total) 0 (used) 6996296 (free)
This can of course change if you use lots of applications in parallel or just never close them. So maybe try the "free" command again when you have lots of things open (browser, media player, games) and see if the swap usage goes up.
Actually I think you wouldn't need swap at all but to be safe I recommend 2GB.

I also found this for you:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
It covers your backup question and also gives this link:
[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)
which tells you how to reinstall the boot manager after you moved the system to another partition

This is specific about the topic of moving a boot partitions content but I personally prefer the other way because I do not feel good about the reliability of copying with dd and resizing the partition:
[http://ubuntuforums.org/showthread.php?t=599599](http://ubuntuforums.org/showthread.php?t=599599)

---

### Post by Liviu-Theodor on 2008-10-30
For using your old Windows partition in Linux, without risking other partition(s) you have, do the following (when I say run a ```
, that means using the CLI):
1. Run [FONT="Courier New"]System->Administration->Partition Editor[/FONT]
1.a. If you don't have it, run:
[CODE]sudo apt-get install gparted
```
2. There, use the free space as you wish, declare what partition(s) you want, and format them with the filesystem you wish (usually ext3).
3. run:
```
sudo blkid
```
Now you have a list of partition UUID's
4. backup your /etc/fstab file:
```
sudo cp /etc/fstab /etc/fstab.backup
```
5. now edit it:
```
gksudo gedit /etc/fstab
```
From the list obtained at point 4, write down in the [FONT="Courier New"]/etc/fstab[/FONT] file what is needed to access your new partition(s). Note also that it is possible to create empty folders with the same name as the mounting points of the new partitions.

---

