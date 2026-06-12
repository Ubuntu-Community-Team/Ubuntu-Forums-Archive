---
title: "How to install dual boot w/Vista"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by S@nctus on 2008-03-06
I have a live CD that I made myself.  I have run Ubuntu from it a few times, and I really love it.  I want to install Ubuntu on my laptop with Vista Home Basic already on it -- so that I can boot up either OS that I choose.

What do I need to do?   I'm afraid of doing something wrong and messing up my system (it did not come with a restore CD or anything)

Thanks for advice.

---

### Post by confused57 on 2008-03-06
> **S@nctus said:**
> I have a live CD that I made myself.  I have run Ubuntu from it a few times, and I really love it.  I want to install Ubuntu on my laptop with Vista Home Basic already on it -- so that I can boot up either OS that I choose.

What do I need to do?   I'm afraid of doing something wrong and messing up my system (it did not come with a restore CD or anything)

Thanks for advice.
You could use EasyBCD, then set up Vista's bootloader to boot Ubuntu:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

First thing you would need to do is use Vista's "built-in" partitioner to free up space for Ubuntu...make sure to install grub to the root partition during the install...you can do this by clicking on the "Advanced" button in the lower right of the install screen(near the end of the install), then you can type in /dev/sda2(or however the partitioner/installer recognizes your root partition)...the default is (hd0), which is the mbr.  Installing to (hd0) would overwrite your Vista bootloader on the mbr.

Don't type in /dev/sda, which the same thing as (hd0)...

Added:  Almost forgot, it would be highly advisable to download & burn a copy of Super Grub Disk, before you install Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by S@nctus on 2008-03-18
Hi!  Thanks for the reply, but I am so new to this I cannot understand what the step-by-step instructions are.  Do you mean:

[LIST]
[*]use Vista's partition tool to create a partition for Ubuntu (if so, how exactly do I do this?  I have two partitions already -- one contains restore and the other just everything.  How do I know how much space to allocate to Vista and how much to Ubuntu?)
[*]then, burn a Super Grub Live CD (what is Super Grub and what do I do with it after I have burned it?)
[/LIST][LIST=1]
[*]What is all this typing about?  Where would I type it?
[/LIST]

Sorry if this is really pitiful.  I wish there were some very simple steps or directions for total newbs somewhere.  I have done searches but can't find anything that really explains.  I appreciate your help.

---

### Post by confused57 on 2008-03-18
It's a good idea to use the Ubuntu live cd for a period of time, in order to get used to using the OS...so it's wise not to be in a hurry to install Ubuntu.

One reason to burn a copy of Super Grub Disk is that it is capable of restoring Vista's IPL(Initial Program Loader) to the mbr if you need to.  You may want to read through the link I gave you earlier...download the iso:
[http://www.supergrubdisk.org/index.php?ind=news&op=news_show_single&ide=2](http://www.supergrubdisk.org/index.php?ind=news&op=news_show_single&ide=2)
Your cd writing software should have an option to burn the iso "as an image", don't burn it as a data or bootable cd...burn it at a slow speed(8x or less).  You shouldn't need to use it, but it will be handy to have if you have boot problems.

This link may help for resizing your Vista partition, using Vista's built-in partitioner:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
after resizing, boot back into Vista to make sure Vista boots OK, it may need to do a
ckdsk.

I would recommend creating approximately 15 Gb of free space, you would probably then need to check "Manual" partitioning(don't select entire drive) in the Ubuntu installer:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
You'll need a / (root) partition of approx. 14 Gb, select primary partition, format as ext3, mountpoint /...and a swap partition, select logical(or extended) partition, mountpoint swap(formatted as swap?).
There is an "Advanced" button on the lower right part of the screen near the end of the installation that you can click on, change the default (hd0) to /dev/sda2(or however the partitioner recognizes your root partition...make a note of how it's designated when you're doing the partitioning step).

Then boot into Vista, download EasyBCD(see the link I gave you earlier)...then follow the instructions in the link I gave you in my previous reply to set up Vista to boot Ubuntu.

I don't have Vista installed, so I can't provide any personal experience for using EasyBCD...this should give you some idea of what you need to do and maybe someone who has actually used EasyBCD will give you some additional instructions, based upon their experiences.

As I mentioned, don't be in a hurry and do your research before you try setting up a dual boot.

---

### Post by S@nctus on 2008-03-18
Thanks for being really patient and breaking all of that down for me.  I'll go back through this really slowly and read up before I give it a try.  It is starting to sound sensible now so I guess that's good :shock::)

---

### Post by confused57 on 2008-03-18
> **S@nctus said:**
> Thanks for being really patient and breaking all of that down for me.  I'll go back through this really slowly and read up before I give it a try.  It is starting to sound sensible now so I guess that's good :shock::)
Glad to help get you started, the more experienced users in the forum are very patient and willing to help new users get started...don't hesitate to ask questions if anything is unclear.

You can see your current partitioning by booting up the Ubuntu live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a lowercase "L"

Make a note of how your Vista partition is designated, e.g. /dev/sda1, /dev/sda2, etc.
This is important to know, so that you don't install grub to the Vista partition, when you click the "Advanced" button during the installation.  So make sure to carefully make a note of your Ubuntu root partition during the installation/partitioning(/dev/sda2, /dev/sda3, etc)...this is where you want to install grub, instead of the default (hd0), which is the mbr.  Even if you accidentally installed grub's IPL to the mbr, you "shouldn't" have any problems using SGD to reinstall Vista's IPL to the mbr. In fact, you may end up wanting to use grub to boot both OSes when you become more experienced with Ubuntu.

If you were to install grub to Vista's partition, you would need a Vista install disk to recover your Vista bootloader:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

See the first link in my signature for another great site to get you started:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

