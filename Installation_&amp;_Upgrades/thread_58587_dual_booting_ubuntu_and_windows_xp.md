---
title: "dual booting ubuntu and windows xp"
date: 2005-08-20
forum: Installation &amp; Upgrades
---

### Post by blacklantern on 2005-08-20
I'm totally new to linux, and definitely new to ubuntu. At first I was planning to build a cheap machine with which I could play around with ubuntu, but now I'm highly interested in installing ubuntu alongside windows in a dualboot setup. I've never installed two operating systems on the same comp before, but I've been seeing things about partitioning hds with windows running on one partition and ubuntu running on the other. Forgive me if this question has been asked before, but how does one create a dualboot setup? Do I have to partition my HD? And if I do, how small can those partitions be? I want minimal space for windows and minimal space for ubuntu, to make future reformats less painful.

---

### Post by Daniel Rehm on 2005-08-20
I would partition the drive, install Windows first, then Ubuntu. If you do Windows after Ubuntu, it (Windows) will eat your bootloader so that even though Ubuntu is still there, you can't boot it.

---

### Post by Velox Letum on 2005-08-20
I used two separate drives to save myself the need of shrinking my NTFS partition.

---

### Post by mcmuffy on 2005-08-20
If you are going to be running windows and linux from the same drive make sure that windows is installed 1st as if you install it after linux windows overwrites your boot loader.

As for how big to make the partition that is upto you. Just create some free space with no file system on it and tell the installer to use that, it will then sort out partitions and formats for you.

---

### Post by Velox Letum on 2005-08-20
Also if you decide to shrink your Windows partition (if it already exists) be sure to defragment first!

---

### Post by blacklantern on 2005-08-20
Okay, some followup questions:

-How do I go about installing and using GRUB? Will I even be using that to choose which OS I'm using?

-My ISP will be giving me some software that I have to install before my account will be activated. I'm assuming that it's not going to be linux friendly. Is there a way around that?

-Is there any linux-compatible software that will allow my linux machine to interact with my ipod?

-there are other things that I normally do on windows that I'm worried about doing in linux. will I be able to watch .mov files, or rip dvds with things like dvdshrink?

Sorry to bombard this thread with other questions, but I figure I can knock all this out in one shot.

EDIT: NM about the quicktime question--I found Mplayer. *laughs* Maybe i should look around these massive forums first before asking a question.

---

### Post by mcmuffy on 2005-08-20
> 
-How do I go about installing and using GRUB? Will I even be using that to choose which OS I'm using?


Grub will set itself up during the install. Upon boot you will be given a menu asking you to choose which OS to boot into.

> 
-My ISP will be giving me some software that I have to install before my account will be activated. I'm assuming that it's not going to be linux friendly. Is there a way around that?


I have to pass on that as my modem just connects to my nic and has its own IP address.

> 
-Is there any linux-compatible software that will allow my linux machine to interact with my ipod?


I plugged my brothers ipod into my pc and it picked it up as a removable storage device which could be written too and I have seen a program called gtkpod that lets you manage songs and playlists.

> 
-there are other things that I normally do on windows that I'm worried about doing in linux. will I be able to watch .mov files, or rip dvds with things like dvdshrink?


Yes .mov files work with the right codecs installed and dvdshrink runs in linux via wine (see [www.winehq.com)](www.winehq.com)).

---

### Post by Storm Rider on 2005-08-20
A note about dual booting.  If your using one hard drive, let Ubuntu resize and partiton your drive. There's no need for Windows apps like Partition Magic.  Unlike Windows, Linux will boot from a "logical" partition.  When given the choice between making the partiton Primary or logical, my recommendation is to choose logical.

It's really not that hard, just give your self a few minutes to read the options.  They'll most likely seem obvious to you.

---

