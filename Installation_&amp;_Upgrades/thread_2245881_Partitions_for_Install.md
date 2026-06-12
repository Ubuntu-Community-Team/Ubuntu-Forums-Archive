---
title: "Partitions for Install"
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by pjnoxon2 on 2014-09-26
Hi,

Installing Ubuntu Studio on my laptop and also XUbuntu 13.10 on a Odroid U3, asking about partition sizes.

On the laptop, I have already these partitions:
      200 MB - EFI
      143.47GB - OS C: NTFS
      341.80GB - Data D: NTFS
      213.05GB - unallocated
So I would make a root, a swap, and a /home for Ubuntu - how big should they be?
(I would like to leave room for later on putting a XUbuntu install and a Mint install as well)
I use the D: for all the data - files I create with applications or download from the internet
and I would put my Linux data files here as well, I guess using Samba to access the NTFS?
      /swap - 6.2GB just larger than my RAM - will the other installs use this as well?
      /home - realistically how big does this need to be?
      /  -  I expect something like 30GB should be more than adequate?

Now with the Odroid, things are a bit more interesting. It has two memory areas, both are
Flash based - one is called an eMMC with (supposedly) 160MB/s access, and a micro SD.
Both are 64GB maximum capacity. There will be no Windows, of course, just Linux. The
XUbuntu 13.10 is 'pre-installed' on the eMMC or on the SD (Actually I have two Odroids).
      /swap - 2.1GB - just larger than the RAM (it is a Samsung Exynos quad ARM core SoC)
      /home - I suspect there will actually not be any home, but read below
      /  -  I expect this all to live on the rest of the eMMC

So I plan to use Odroid for a sandbox Moodle server, so I need to install LAMP and Moodle.
I expect to put all these on the eMMC and the course files on the SD. Sound reasonable?

thanks - PJ

---

### Post by yancek on 2014-09-26
> So I would make a root, a swap, and a /home for Ubuntu - how big should they be?

The standard method for Linux installs for years was simply a root partition and a swap partition.  Lately, more systems have been offering to create a separate /home partition as well which you can do during the installation.  The sizes are pretty much up to the user, 15-25GB for the root, you may not need a swap depending upon how much RAM you have but 2-6GB should be more than enough if you have  a large enough drive.  Most users who create a separate /home partition create it as much larger than root as that will generally be where all your personal data is, photos, movies, music, documents, etc.  Some users just create a separate data partition, it's all optional.

You already have a data partition with a windows filesystem which you can mount and access read/write from Linux.  If you feel you need more space for shared data, use ntfs as the filesystem and you will be able to access it from windows and Linux.  If you use a Linux filesystem, windows will not see it unless you install third party software.  You use ntfs-3g which should be installed and do not need Samba which is used on networked computers not the same computer.

I don't know what Odroid is so someone else can try to help with that.  You do know that Xubuntu 13.10 has reached end of life and is no longer supported.

---

### Post by pjnoxon2 on 2014-09-26
Ahh, thanks so much. So in using the D:Data (NTFS) for photos, movies, music, documents, and the like, no need
for a /home for those then. What else goes normally in /home and not in /  (the root) then? Nothing, or just a few
other odds and ends like preferences, bookmarks, options, and application housekeeping items perhaps? That would
mean the /home should be quite small.

Once I install a Xubuntu and Mint, they will each need their own root (/) but will they also need their own /swap
and of course the most important question, do they each need their own rather small /home?

much obliged - PJ

I'll check into the Xubuntu version.

---

### Post by yancek on 2014-09-26
The /home partition actually is usually larger than the root filesystem.  There are user configuration files there and a user has read/write access to anything in the /home directory which simplifies things also.  I would make the /home partition at least the size of root filesystem but that's up to you.  You only need one swap partition whether you have one operating system or 10-20 systems. Sharing a /home partition between two or more operating systems can lead to complications although some people do it.  Mostly it is people with a lot of experience.  You don't need a separate /home partition, just leave home in the root partition and create data partition or leave unallocated space on which to create them later as needed.

I always just create a root partition and then have several data partitions for different types of data but that is just a personal preference.  You can do it either way.

---

### Post by pjnoxon2 on 2014-09-26
That's good advice, just a root and no /home for each distro.

Pity me - learning everything at once: Ubuntu, Apache, MySQL, PHP, Moodle, ...

Thanks so much - PJ

---

### Post by pjnoxon2 on 2014-11-18
I'm back at it. I haven't done the install on my Laptop yet (I'm a scare-dy cat and don't want to brick it).

But I have my Odroid computers now. I want to install moodle on one and I was recently told that if the
Ubuntu distribution 'knows Moodle' this will make everything easier and more easily upgradable. Just enter:

sudo apt-get update
sudo apt-get install moodle

and this is supposed to install Apache, MySQL, PHP with all the needed extensions, and Moodle.

The Moodle website does not say this, but perhaps it is more generic for various Linux distros...
Also is there any essential difference between Ubuntu Server and Ubuntu (not-server)? I think
this Odroid is actually Lubuntu or Xubuntu and you can turn off the Xwindow when you want.

Anyone know if the "sudo apt-get install moodle" will actually work as suggested?

yours - James

---

### Post by pjnoxon2 on 2014-11-18
I tried "sudo apt-get install moodle" and it installed everything.
It installed postgresql instead of mysql, but I don't
know either one so it doesn't matter to me.

- pj

---

