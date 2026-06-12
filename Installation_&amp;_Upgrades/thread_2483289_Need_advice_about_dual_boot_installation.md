---
title: "Need advice about dual boot installation"
date: 2023-01-25
forum: Installation &amp; Upgrades
---

### Post by alfredlarsson on 2023-01-25
I want to install Ubuntu alongside Windows but I'm unsure what's the best way to set it up.

I currently have a 100 GB SSD (C: ) on which Windows is installed, and a 1 TB HDD (D: ) where I install most programs and store personal files. Ideally I'd like to have one partition for Windows programs, one partition for Ubuntu programs and one partition for personal files that is accessible from both operating systems. Right now, about 80-90% of the SSD is taken up by Windows system files and programs that don't let you choose the installation path, so I don't think I could make space for Ubuntu on it. 

I installed Ubuntu for "practice" with a 4 GB swap partition and ~140 GB root partition (all on the HDD). I noticed that all files on the Windows D: partition are accessible from Ubuntu, both personal files and also program files from installed Windows applications (which is useless on Ubuntu, obviously). I will most likely replace this old computer with a new one pretty soon, but I wanna figure out the optimal configuration now so that I know what I'm doing on the new machine. (I'll probably just get a single, larger SSD for the new one which might be more straight forward, but still.)

Any thoughts, advice or opinions would be appreciated. :)

---

### Post by TheFu on 2023-01-25
Don't dual boot.  Use a virtual machine and put the OS you don't need fast graphics into the VM.  That way, you can use both, concurrently.  Also, VMs don't allow direct access to hardware, so they see "fake" hardware that is the most supported models. The VM won't have any driver issues, which can be really nice if you have unpopular hardware.

About once a year, MSFT updates will break a dual boot setup. Beware.  Of course, that won't happen when it is convenient. ;)

So, my advice is not to dual boot.  I stopped about 2008 and have been running OSes inside virtual machines since a few years before then.
Even though I've been running Linux systems since the early 1990s, I didn't really have a linux desktop until 2006-ish.  Initially, I put Linux inside a VM running under Windows.  Around 2010, I switched to running Windows inside a Linux hosted VM.  I still do it that way and don't have regrets, except some of my old games from pre-WinXP are a hassle to use.  I haven't tried too hard to get them working, but it isn't just pull up a Win2000 VM and install.  
Newer games that want direct access to the GPU would need a different solution. Others here have much more experience with GPU passthru to a VM than me.

How best to allocate storage isn't easy to optimize, since we all have different needs and even if you have an idea what you need, 12 months from now, it will be different. I've never guessed right in almost 30 yrs. These days, I go with the most flexible solution possible. One that can be easily changed as needed.  
That's LVM2:
[https://www.howtogeek.com/36568/what-is-logical-volume-management-and-how-do-you-enable-it-in-ubuntu/](https://www.howtogeek.com/36568/what-is-logical-volume-management-and-how-do-you-enable-it-in-ubuntu/) and 
[https://www.howtogeek.com/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/](https://www.howtogeek.com/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/) 
The articles are a little old, but all the LVM commands are still correct.  Installing Ubuntu with LVM is a checkbox option, but that will wipe the entire drive - not good for dual boot, since it will wipe other OSes too.  If you don't want to do that, then you'll need to manually setup all the LVM objects - PV, VG, and LVs as desired.  It can be complicated, especially for someone without at least intermediate skill with Unix/Linux administration.  

Dual booting causes all sorts of complexities. Those can be easily avoided by using virtual machines instead.

---

### Post by tea for one on 2023-01-26
> **alfredlarsson said:**
>  I will most likely replace this old computer with a new one pretty soon, but I wanna figure out the optimal configuration now so that I know what I'm doing on the new machine. (I'll probably just get a single, larger SSD for the new one which might be more straight forward
If Windows 10/11 were important for me, I would buy a PC where I could install two disks.
Each OS on a separate disk.
Boot either via UEFI boot menu. (avoid shared bootloaders/managers)
Create shared ntfs partition (if required) in Ubuntu.

Having said that, my PC has Ubuntu 22.04 host and Windows 11 VM as guest.
Windows is only used as a test/play device - not essential for my computing needs.

---

