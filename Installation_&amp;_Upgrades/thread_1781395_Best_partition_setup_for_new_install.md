---
title: "Best partition setup for new install"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by Warthaug on 2011-06-13
In a few weeks I'll be building my first ever non-dual-boot ubuntu system.  Because I've been using dual-boot (ubuntu/windoze) systems my partition setup has been limited due to the need to share partitions and partition limits in general.  Now that I'm doing a pure-linux install, I have a few questions about various setups I've seen, and which ones are better for my use.

To be clear, the computer will be a desktop computer, no servers or shared resources are expected to be hosted on it.  About the only non-standard thing will be Win7 inside of virtualbox.

What I was wondering is what type of partition setup is best for this kind of use?  I know a separate /home partitions (plus the usual /swap partition) are normal, to ease upgrades and backups.  However, I've seen a few resources recommend a separate /boot partition as well, and some mount other directories as separate partitions in addition to swap, /home and /boot.

In particular, I was wondering what the advantages of mounting /boot as a separate partitions was, and if it was worth it give the type of system I am building.  I will be mounting home as a separate partition; no need to convince me of the usefulness of that ;)

Thanx


Bryan

---

### Post by oldfred on 2011-06-13
For standard desktops, I do not believe in a separate /boot. I also now leave /home inside root and create separate /data partition(s). I think Herman also now does not even have a separate swap but uses a swap file.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Even my own optimal partitioning scheme is not so optimal a couple of years later. But I do not believe in hard disk durability so every 3 years add a new drive, use old drive as short term backup and still backup most important data regularly (but not as often as I should) to DVDs to have an archive & off site backup.

If a very large hard drive there is some small advantage to having all the system files including the user setting in /home in a smaller partition so drive does not have to search entire drive.  We have seen users with 1 or 2TB drives and have part of the boot files at the beginning of the drive and part at the end with only one very large / partition.

Shared /data -see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
With upstart script 
[http://ubuntuforums.org/showthread.php?t=1771773&page=5](http://ubuntuforums.org/showthread.php?t=1771773&page=5)

---

### Post by SeijiSensei on 2011-06-13
I always keep a small separate /boot partition (512 MB is the max you'll need) because I usually have a separate partition for any distributions I might be testing.  So, in general, I'll have:

/dev/sda1  512 MB  /boot
/dev/sda2  2-4 GB    swap
/dev/sda3  extended

/dev/sda4  20 GB   / for distro in use
/dev/sda5  20 GB   / for distro being tested

/dev/sda6  20 GB   /usr/local (for scripts and programs built from source)

/dev/sda7  rest    /home

That way I can install a second distro in /dev/sda5 and have it be added to the boot menu automatically during installation.

---

### Post by aeronutt on 2011-06-13
> **SeijiSensei said:**
> I always keep a small separate /boot partition (512 MB is the max you'll need) because I usually have a separate partition for any distributions I might be testing.  So, in general, I'll have:

/dev/sda1  512 MB  /boot
/dev/sda2  2-4 GB    swap
/dev/sda3  extended

/dev/sda4  20 GB   / for distro in use
/dev/sda5  20 GB   / for distro being tested

/dev/sda6  20 GB   /usr/local (for scripts and programs built from source)

/dev/sda7  rest    /home

That way I can install a second distro in /dev/sda5 and have it be added to the boot menu automatically during installation.

Rookie question: So with a separate boot partition, when you load a new distro on a different partition, how to you get Grub to not load during the new distro install?

---

### Post by Warthaug on 2011-06-13
Thanx for the replies.

I did not mention this, but I need to encrypt the home folder because it will contain patient data; so a separate partition is my best bet.

I'm still not clear why some use a separate /boot partition.  It sounds like I don't need one, but inquiring minds want to know...

Bryan

---

### Post by oldfred on 2011-06-13
With new systems it may be required if the install uses a new file system not fully supported by grub & the boot process (BTRFS, maybe still?).  Old grub from other distribution or Ubuntu before 9.04 will not work with ext4 formats.

Many servers also use a /boot to keep it outside the RAID or LVM.

Old system with a 137GB boot limit required the bootable partition  inside the first 137GB. When users added a larger hard drive and had  windows in the first part of the drive, you often had to create a small  boot partition.

---

### Post by el_koraco on 2011-06-13
+1 on /home inside /, and keeping a separate /data. That way, you can actually create the Documents, Videos, etc. folders in /data ad symlink it to /home/username. Plus, your data is tucked nicely away from the main system, so in case of reinstalling you don't risk Ubiquity wiping your data on a "mount, but don't format" /home partition (it's been known to happen), and you don't have config files giving you trouble on fresh installs.

---

