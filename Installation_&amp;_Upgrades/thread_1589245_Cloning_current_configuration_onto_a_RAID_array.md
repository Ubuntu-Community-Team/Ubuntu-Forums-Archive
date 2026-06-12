---
title: "Cloning current configuration onto a RAID array"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by seeyouza on 2010-10-06
Hi all

I'm going to be creating a RAID-0 array comprised of 3 disks, which will be 1.5TB in size. My current drive is a single 1.5TB disk, configured as follows:

[IMG]http://img839.imageshack.us/img839/4687/hddconfig.jpg[/IMG]

The 1.2TB partition is a data partition accessed by both Windows 7 and Ubuntu.
The EXT4 partition is obviously Ubuntu, as is the swap space
The 79GB partition is Windows7

Currently, GRUB is managing my dual boot, and everything is working 100%.

My plan was to simply clone the current drive onto the raid array using something like GParted. I know Windows7 would probably work after the operation, but I'm not sure how it would affect Ubuntu, so I'm looking for some advice.

Obviously the point of cloning would be to avoid the reinstall and reconfiguration of everything. I wouldn't mind reinstalling W7 as it's basically just my gaming OS and would be quick and simple. But Ubuntu is my main environment and development machine, and is set up with all my tools, web server and virtual host configs, etc.

So the question is two-fold - would Ubuntu actually WORK after an operation like this (ie. would it support the RAID array out of the box), and if not, how would I go about installing Ubuntu onto a RAID array and easily transfer my current configuration across to the new install, keeping in mind I need to dual boot with Windows?

Thanks in advance

---

### Post by wkulecz on 2010-10-06
> I know Windows7 would probably work after the operation

Not unless you use "fake raid" aka DM raid where you setup the array via your BIOS.  Usually this needs drivers added during the installation which means you will likely blue-screen after the data cloneing.

Three disk RAID-0?  That will reduce reliability by 3X, not what I'd recommend for a development system!

My experience with RAID-5 suggests you risk losing everything with a single drive failure unless you are expert at recovery with mdadm commands or your bios's equivalent in the case of DM raid.  Fortunatley I had good rsync backups and that is what I do now without the raid. 

My "failure" was a loose power connector on one drive in the array (after moving the box across the room) and the net result would have been total data loss disaster without my backup!  Unless you are willing to study the failure recovery options beforehand, you are better off putting the effort into a robust backup strategy instead of hopeing you can figure out how to recover from a raid failure after it happens!

I have video editing on a dedicated windows 7 box and I use fake raid-1 there becuase of the hassle of reinstalling and activating it, but for linux, just use rsync from a cron job to clone the disk and learn about re-installing grub and you wil be IMHO way better off.  It has wasted many hours "rebuilding" after a power glitch, but it did seem work -- UPSes don't alwyas detect the batteries are bad until its too late :(

---

