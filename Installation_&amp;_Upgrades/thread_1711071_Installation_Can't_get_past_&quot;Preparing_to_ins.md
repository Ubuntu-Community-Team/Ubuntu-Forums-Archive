---
title: "Installation: Can't get past &quot;Preparing to install Xubuntu&quot;"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by chockopocko on 2011-03-20
Sorry if all the advanced users, especially the two who answered my last post see this and find it annoying. Linux novice here. Thanks, Hedgehog1 and morgaes, by the way, for answering my last post. 

Anyways, I basically have the same problem as in my [last post](http://ubuntuforums.org/showthread.php?t=1703917). 

A few changes though/Quick summary:

I am trying to install Xubuntu this time, which only requires 192 MB of RAM to install, instead of Ubuntu.

I could try using Xubuntu with the Live CD, except it was very slow as well. Things ran though.

I could get to the screen, "Preparing to install Xubuntu." I have all the requirements met: 2.6 MB available on the hard drive, power, and Internet access. I click forward, choosing to install third-party software, and download updates while installing. It froze. 

Any help is much appreciated. As well, I am thinking about using the Xubuntu Alternate CD (64 MB RAM required), or install Lubuntu, but am hesitant to burn another CD. Didn't buy the CD-RWs, and am regretting it, though I've heard CD-Rs are better. 

-- 
Microsoft Windows XP Home Edition
Dell Optiplex GX260
X86
Total Physical Memory 256 MB
Available Physical Memory 12.05 MB
Total Virtual Memory 2 GB
Available Virtual Memory 1.96 GB
Page File Space 625.10 MB

---

### Post by TexasRussian on 2011-03-20
You may wish to run it via live CD, then install it while in the live CD mode. If that doesn't work, then I don't know, the only thing I can think of is the ram, but it seems as though you have sufficient memory.

---

### Post by chockopocko on 2011-03-20
Well, I tried that. It was very slow though; nothing was happening. 
No offence, but I'm not sure how that would work?

By the way, I'm trying to install without the quiet screen-- in Advanced Options.

Something weird is going on.. when I quit the graphical installation, for the second time - it went into the live CD. Now i'm quitting the graphical installation for the third time. It says "Installing..." 

As well, when I had checked if this was a defective CD, it said, ```
keys:Press any key to reboot your system
``` or something like that.

---

### Post by chockopocko on 2011-03-21
Now, I've tried editing the Boot Options - erasing ```
quiet screen--
``` and put in ```
acpi=off
```. When I tried to get past the "Preparing to Install Xubuntu" screen, there was an error message saying that "ubi-prepare failed with error code -9". The information is in some file in "/". 

Any help please?

---

### Post by nunrgguy on 2011-05-06
I've come across this recently with Xubuntu and Lubuntu. Funnily enough plain Ubuntu worked fine BUT was far too slow on the system.

The way I found to get X to install (still had no joy with L) was to NOT select download updates and install 3rd party - it's that that is causing it to hang.

---

### Post by frisket on 2012-12-01
> **nunrgguy said:**
> I've come across this recently with Xubuntu and Lubuntu. Funnily enough plain Ubuntu worked fine BUT was far too slow on the system.

The way I found to get X to install (still had no joy with L) was to NOT select download updates and install 3rd party - it's that that is causing it to hang.

I can confirm the identical problem using XUbuntu 12.10 burned to a USB, with the exception that it still hangs even if those options are left unchecked.

I am therefore stuck: short of burning a CD (which I doubt will make any difference: this looks like a bug in the program, not a corruption of the disk), I now have no way to install Xubuntu 12.10 (the machine is currently on Ubuntu 12.10 but its too slow)

Is there *any* way to install Xubuntu 12.10 if the installer in the ISO is broken?

---

### Post by frisket on 2012-12-11
> **frisket said:**
> I can confirm the identical problem using XUbuntu 12.10 burned to a USB, with the exception that it still hangs even if those options are left unchecked.

I am therefore stuck: short of burning a CD (which I doubt will make any difference: this looks like a bug in the program, not a corruption of the disk), I now have no way to install Xubuntu 12.10 (the machine is currently on Ubuntu 12.10 but its too slow)

Is there *any* way to install Xubuntu 12.10 if the installer in the ISO is broken?

I re-downloaded the ISO as a single file from one of the mirrors instead of using the torrent. That burned fine, and installs fine.

So forget using the .torrent, download the ISO as a whole file.

---

