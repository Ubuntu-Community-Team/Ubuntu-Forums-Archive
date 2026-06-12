---
title: "How is Quad boot with Unbuntu Possible"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by tsam19 on 2010-09-15
Hello again

I have appealed to anyone on this forum site for any help on installing Unbuntu 10.04.1 LTS on a MACBOOK PRO (Mid 2007 Model.

Basically I've followed a few threads & posts on how to Quad boot a Macbook Pro & it seems pretty straight forward,however....

Ubuntu is not playing ball for some reason??

The first attempt I tried I had the partitions as follows:

I am using a 500gb sata internal hard drive.

WIN 7 - 125gb
STORAGE - 15gb
WIN XP -125gb
MAC OSX - 180gb 
FREE SPACE  50gb - Formatted DOS - Which would become the EXT4 & SWAP FILE partition.

After following instructions:

[http://hydtechblog.com/2009/01/26/dual-triple-quad-boot-a-macbook-with-mac-os-x-ubuntu-linux-windows-xp-and-windows-vista/](http://hydtechblog.com/2009/01/26/dual-triple-quad-boot-a-macbook-with-mac-os-x-ubuntu-linux-windows-xp-and-windows-vista/)

I managed to get 3 operating systems working & bootable from the rEFIt boot menu on initial start up.

I proceeded to install unbutnu, but the unbuntu installation system  files ended up in the WIN XP partition??

Rendering WIN 7 unbootable from the rEFIt page & no boot menu ICON?

The WIN XP partition ended up being reduced from 125gb to 65gb & the Ubuntu SWAP file partition ended up inbetween the MAC OSX & FREE space partitions?

Eventually the WIN XP partition wouldn't even boot, So I deleted the WINDOWS Partitions all together & started a fresh.

I understand Ubuntu needs TWO partitions, one for the system file & the other for the SWAP file.

How or what choice do you make from the partition page to get UBUNTU to install on the same (one) partition & for it to BOOT correctly?

That is to get all system (EXT 4) & SWAP files on the same partition?


I tried installing Unbuntu again, with ONLY MAC OSX installed (no windows installed) this time taking care to choose the correct 'DEV/SDA7' partition from inside ubuntu disk partitioner 'DEV'SDA7 being the last FREE SPACE partition I wanted all the ubuntu files to go into.

I took the remaining 50gb FREE SPACE & partitioned enough for the system files.
The remainder was partitoned for the SWAP FILE, but BOTH partitions were in the same 50gb file space.

On the boot loader page I chose DEV/SDA7 as thats where the system was going to originate from.

Installed the operating system & followed the on screen instructions, only to get yet another 'DISC error' message all down the screen!!

And yet another PENGUIN on the rEFIt boot page!

I have looked at the Unbuntu Docs site (on here) for installation information & tips, but to no avail.

I'm wondering if its worth the hassle?

It doesn't seem to be as straight forward as some people make out, I'd say by far MAC OSX, WINDOWS are by far the most easiest operating systems to install.

If anyone can shed some light on the correct way to install Unbuntu so it boots up, It would be nice to get some feedaback.

---

### Post by tsam19 on 2010-09-15
Some more pics on the matter, if anyone can decyher them.

---

### Post by Elfy on 2010-09-15
> That is to get all system (EXT 4) & SWAP files on the same partition?You can't - nor can you make a windows partition ntfs and fat32 at the same time - which is in effect what you are trying to do. They are completely different filetypes - linux-swap and ext4 (or whatever filteype you are trying to use).

You can though install without swap assuming you have sufficient RAM. Use the manual partitioner option and install to whichever partition you want to - make sure to Edit the partition to format it to a linux filetype. Also ensure you set the mountpoint to /.

Once you have installed - if you then wish to create a swap file rather than partition you can do that. [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

---

### Post by tsam19 on 2010-09-15
I have Macbook Pro Intel 2.2ghz, (Mid 2007 model) 4gb of RAM, is that enough to have without using a SWAP File partition?

Why are there so many file type extensions for Linux, ie EXT3,EXT4 etc?

Which one do I choose for Ubuntu 10.04.1 LTS or Ubuntu Ultimate 2.7?

The link I provided in my opening post, the instructor is using an older version of Ubuntu - V 8.04.1 or similar.

If you follow their last part on how to configure & install their version of ubuntu, do their instructions apply to the version I am using Ubuntu 10.04.1 LTS?

As they use both the SWAP file & EXT 3 on their last partition.

I did use the partitioner tool as in the instructions, but it didn't work for some reason, probably because after further research.

In the boot loader page before install began, I typed in (hd2,0) or similar, which I NOW presume was a direction to 'partition 2', which already had WIN XP installed onto it & which would now explain why WIN XP & WIN 7 became corrupted & wouldn't boot up from the rEFIt page.

I do admit I am only a Linux beginner, and the more feed back I get the better I will have of understanding how this system works, especially installing it.

So basically if I have a partition of 50gb left at the end of my hard drive, I can format the whole 50gb to the Linux file system ext needed & then install Ububntu 10.04.1 straight onto it, with no problems?

What about the boot loader page, do I choose the formatted DEV/SDAx partition?

Or do I type in something else?

If I choose to make a SWAP FILE in line with the parameters on the link you gave.

So If I choose 2GB SWAP FILE, where do all the SYSTEM FILES go?

---

### Post by Elfy on 2010-09-15
I have no idea how refit works I'm afraid - but you could install grub to a partition - for example dev/sda1 

I use ext4 and have had no issues with it.

The reference to hd0,2 would need to be the partition linux is installed to.

> So basically if I have a partition of 50gb left at the end of my hard drive, I can format the whole 50gb to the Linux file system ext needed & then install Ububntu 10.04.1 straight onto it, with no problems?Yes - and probably - you might get problems - but it's hard to second guess that.

---

### Post by oldfred on 2010-09-15
You may do better in the Apple forum
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

I do know the Macs use gpt partitioning while most of the rest of us are using MBR(msdos) old style partitioning. Windows will read gpt partitions but not work in them, so you have to have a hybrid partition scheme where the first three partitions are made to look like MBR, so windows will work. The remaining partitions are gpt. But hybrid is a kludge and has many issues.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by Elfy on 2010-09-15
> **oldfred said:**
> You may do better in the Apple forum

I thought that was a good point - I often forget that forum, but it looks like the OP has a thread in there already.

[http://ubuntuforums.org/showthread.php?t=1573609](http://ubuntuforums.org/showthread.php?t=1573609)

@tsam19 - as the other is a duplicate thread I have closed it. If you want this thread moved to that forum report this one and ask for it to be moved.

---

### Post by srs5694 on 2010-09-15
I'm not an expert on OS X boot loaders, although I do know a thing or two about GPT and hybrid MBR configurations, as I'm the author of [GPT fdisk (gdisk),](http://www.rodsbooks.com/gdisk/) a GPT partitioning tool.

Some of your problems are almost certainly related to the hybrid MBR, which is an ugly kludge; see my [hybrid MBR Web page](http://www.rodsbooks.com/gdisk/hybrid.html) for details. If you can find instructions on installing Ubuntu on a Mac using a conventional GPT, my recommendation would be to do so, and then to install Windows using a hybrid MBR for the Windows partitions. That might eliminate some of the problems.

---

