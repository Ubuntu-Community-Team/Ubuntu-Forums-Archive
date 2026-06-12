---
title: "Common &quot;Can't Access tty&quot; error after fixing GRUB"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by The Bird Man of Alcatraz on 2007-08-31
I'd like to thank everyone for their help in my previous threads, but now that I've finally gotten GRUB working I'm running into the very common "Can't Access tty" bug while loading Ubuntu.

Here's my brief story:

A few weeks ago I tried to double boot Windows 2000 on my proven Ubuntu 6.06 box.  First, I used GParted Live CD to size down my Ubuntu partition.  Ubuntu still worked fine after that.  Next, I installed Windows in the free space of my IDE HDD.  After the installation, I reboot, and the computer says it cannot find any bootable media.  By a few days later, I had finally gotten GRUB working again, and had deleted the Windows partition with the GParted Live CD.  GRUB listed all of my different Ubuntu kernels, and their recovery modes.  I try booting into Ubuntu as usual, and I get stranded in BusyBox.

I've searched and searched for solutions, many of which say GRUB is pointing to the wrong location.  GParted  says my main partition is called HDC1.  I check GRUB, and it is pointing to the right partition.

Here are my specs:
1 GHz Athlon
256 MB RAM
ATI 9200 SE
80 GB IDE HDD
One simple CD Drive

I'd be eternally grateful to the person that can help me out in this pinch.  I'd really, really don't want to loose my work, but I guess I can reinstall if necessary.

**[COLOR="Red"][SIZE="5"]Here's an idea...[/SIZE][/COLOR]**

Can I install Ubuntu 7.04 on the free space of my HDD, and pull my work off of the old partition into the new installation?  I'd be more than willing to do that, and its about time I upgraded anyways.

Thanks a ton!

---

### Post by merlinus on 2007-08-31
A few things occur to me.  First of all, have you installed the drivers for your video card?  There are initially many problems with ATI cards.

Second, look at /boot/grub/menu/lst to see if indeed grub is pointing to the correct partition.  You may have to manually mount your ubuntu partition to do this.

And of course you can always reinstall, but that in and of itself will not fix the video issues.

-merlin

---

### Post by Pumalite on 2007-08-31
What did you install? Live CD? Memory is probably not sufficient.
Better off with Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

