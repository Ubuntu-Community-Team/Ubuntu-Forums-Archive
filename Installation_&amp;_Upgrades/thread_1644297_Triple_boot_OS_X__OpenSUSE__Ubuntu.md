---
title: "Triple boot OS X / OpenSUSE / Ubuntu"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by annoyingpi on 2010-12-13
Hi, 

I have a MacBook that currently dual boots Mac OS X / OpenSUSE 11.3. I want to try out Ubuntu while preserving my OS X and OpenSUSE installations. How would I go about doing this? 

I don't have a lot of linux experience, so I have a lot of (possibly silly) questions:
I need to make a new partition for Ubuntu. Would I make a new partition before installing Ubuntu, or would the Ubuntu installation handle this for me? In addition, does have two linux distributions affect my ability to boot OS X? I assume that I would need to add an extra option in rEFIt. 

I'm planning to switch to primarily using Ubuntu, so ideally, Ubuntu would be able to access my current /home directory. Would the two linux distributions both be able to use the same /home directory? 

Thanks for your help!

---

### Post by zvacet on 2010-12-13
You can install Ubuntu on Mac and during installation proces you will come to the partitioning stage and then you will make partition for Ubuntu.Maybe that will mean to shrink existing partitions.You can use same home for two linux distros,but sometimes you can ger errors,because Opensuse in **rpm** based and Ubuntu is **deb** distro.

---

### Post by srs5694 on 2010-12-15
The single biggest problem you'll encounter is partitioning. Your current setup probably uses the terrible hack known as a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) and unless you *fully* understand what you're doing, making any changes at all to your current partition table is like playing Russian roulette with just one or two empty chambers. Therefore, my recommendation is to install Ubuntu on another physical disk, which will enable installing without messing with your current partition tables. Even a USB flash drive will do, although it'll be slow.

As to sharing the /home directory, first please understand the distinction between the /home directory and individual users' home directories. The former houses the latter, and as Linux is a multi-user system, you can have multiple user home directories in /home (/home/fred, /home/ginger, etc.). Sharing a /home directory is possible if it's currently on a separate partition. Doing this works best if you use separate user home directories for each distribution (say, /home/annoyingpi for SUSE and /home/annoyinge for Ubuntu). This in turn is easiest if you use different usernames in each distribution, but there are ways to use the same username but different home directories. You can change one (using mv and usermod) after installation or use advanced user creation procedures, for instance. Sharing a single user home directory (say, /home/annoyingpi) is inadvisable because different distributions use different versions of various user programs, and may place icons and whatnot in different locations. Thus, programs can malfunction or behave oddly when they read configuration files for the other distribution.

Contrary to zvacet's advice, sharing the /home directory (or even user home directories) has *nothing* to do with the package management system (RPM vs. Debian packages). Packages are installed to system directories, and the package databases are also stored outside of /home.

---

