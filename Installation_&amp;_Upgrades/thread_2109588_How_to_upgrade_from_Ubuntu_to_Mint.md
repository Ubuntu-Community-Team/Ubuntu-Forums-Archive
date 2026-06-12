---
title: "How to upgrade from Ubuntu to Mint"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by efinlaw on 2013-01-28
Ok, since I'm tired of trying to fix my bizarre network problem I've decided to try out Linux Mint to see I get the same issues.

I am currently running a dual boot with 12.04 and Windows 7. I'm not very experienced with manual partitioning and frankly, I'm a little nervous messing with my hard drive. Is there any easy way to upgrade from Ubuntu to Mint? Is there a similar installation process with Mint as in Ubuntu where there is an automatic partition option? Any help would be appreciated.

Here's what my partitions look like now from the windows disk management screen, if that helps at all.
[http://postimage.org/image/h0zuo1m9d/](http://postimage.org/image/h0zuo1m9d/)

Also, if anyone has any more input on the problem I've been having, it's described here:
[http://ubuntuforums.org/showthread.php?t=2107461](http://ubuntuforums.org/showthread.php?t=2107461)

---

### Post by Mark Phelps on 2013-01-28
> **efinlaw said:**
> ...I'm a little nervous messing with my hard drive. ..

Then, BEFORE you do anything else, presuming that you want to be able to recover access to Win7 should anything go wrong during the Mint install, I would boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  AT least that way, if the Win7 boot loader gets corrupted, you will have a CD you can use to restore it.

Also, if you have an external drive, I would download and install the FREE version of Macrium Reflect into Win7 and use it to image it off to the external drive.

Better safe than sorry ...

---

### Post by orb9220 on 2013-01-29
Easier way not relying on Windows at all is [Redo Backup]("http://redobackup.org/"). Dowload 250mb iso and burn to cd. And boot with it. Uses same under the hood engine as Clonezilla but a lot easier to use.

Easy and can back up all your partitions including Windows to another hardrive partition or external usb drive is what I do.

Then I just back up the Linux partitions only. So I can do clean installs of different distro's and then back them up once I have them setup and running with my programs & settings. And only takes me 20 mins to restore linux back to prior distro or full with windows in 40 mins.

And a lot easier and faster than the windows way.

And have Ubuntu 12.10,Mint 14 Cinnamon,Fuduntu,Voyager 12.10 xfce backups on a external usb drive. And last night did a clean install of Linux Mint 14 KDE. Once I have everything installed upgraded and tweaked then will redo backup the KDE 3 linux partitions also.

Then I can swap distro's in 20mins and no hassles. As have done total and just linux restores half a dozen times no issues. Only issue is use the same partitions and don't change the size of the partitions.
.

---

