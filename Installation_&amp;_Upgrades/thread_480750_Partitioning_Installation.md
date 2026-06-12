---
title: "Partitioning Installation"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by CJTDom on 2007-06-21
I am running two Dell Poweredge 6450 Rack Servers, 4 Xenon Pentium III Processors. During installation, it  starts the partitioner, I click guided, and it just hangs on a blue screen forever. I can CTRL-C escape, but it just starts the partitioner again. Any suggestions?

---

### Post by cwgpress on 2007-06-22
> **CJTDom said:**
> I am running two Dell Poweredge 6450 Rack Servers, 4 Xenon Pentium III Processors. During installation, it  starts the partitioner, I click guided, and it just hangs on a blue screen forever. I can CTRL-C escape, but it just starts the partitioner again. Any suggestions?

On one of my early attempts at Ubuntu, I had similar problems. I think I eventually booted from a gparted CD and set the disk up the way I wanted, then did the install again using manual partitioning. On later installations, I've been able to let the installation run along its merry way, starting the partitioner at the appropriate time, but I always use manual partitioning. It's easy to do, and I prefer to have control over it, leaving space for future needs rather than hogging a whole disk.

Good Luck

---

### Post by CJTDom on 2007-06-25
it seems like that yields the same results, it just freezes, and refuses to continue to the next stages. It is quite disheartening, as the reason I am installing Ubuntu is so when I eventually leave my current position, which they are not going to refill (volunteer for school IT), I didn't want to leave them with Gentoo, as I thought it would be much harder to install than gentoo. Oh well, everyone needs a little irony now and again ;)

---

### Post by Pumalite on 2007-06-25
At this point I would start checking the disc or iso. Do checksum. If you have to download: torrent better than HTTP or FTP. Burn at 1x, etc. You could also try 'Alternate CD'. How much memory do you have?. If 250MB or less; try 'Alternate Xubuntu CD'.

---

### Post by cwgpress on 2007-06-25
I have found the 'alternate' installs to be smoother, but then I've been doing computers for a long time (got my M.S. in Computer Science in '81 or so) and command lines are comfortable! I think the alternate installation procedures are a bit less resource-intensive, therefore a bit more forgiving of any peculiarities in hardware. Also if it does happen to freeze you generally can see what happened last, and find a workaround.

Since my last post, I got VMWare up and running under Vista, and installed a 64-bit version of Ubuntu in a virtual machine that's on my 32-bit Vista Home Premium. WAY COOL! There are even options to install the virtual machine in a real physical partition rather than a virtual image that's really part of the NTFS filesystem for Vista; I've been too cautious [timid] to try it. Once I get a second disk attached, I'll probably risk it, but for now I have too much time and effort invested.

Chuck

BTW I think http or ftp are better than torrent, contradicting someone else's comment...

---

