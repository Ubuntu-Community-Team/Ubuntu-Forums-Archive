---
title: "Installation hangs on Vaio w/ PCMCIA CD"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by gpags on 2007-11-21
Trying to install Xubuntu 7.10 on an old Sony Vaio PCG-SR17. Base config: PIII 700MHz w/ 128MB RAM using a PCMCIA CD drive. Due to limited RAM I'm attempting to install from the alternate CD.

Everything seems to go fine until the install hangs at 82% of the base system install at the 'Installing the kernel - retrieving and installing linux-generic...' step. The install never gets past this point (and I've tried many, many times). I've tried slow-burning a couple of different CDs off of different ISO images and always get the same result.

At the point of hanging, the system works for several minutes periodically accessing the CD and HD before it finally stops doing anything and becomes totally unresponsive.

Any ideas? Thanks for your help.

---

### Post by jasahl on 2007-12-14
I'm running into this too (attempting to install on a Pentium 166 - 256MB RAM).  I ran the CD check & everything cleared, so the burn seems to be ok, but it hangs forever on the "installing Linux kernel" item.

---

### Post by Killians1978 on 2007-12-15
I've noticed this on every flavor of Linux. I have a PCG-SR27 and what I've discovered is that the disc is fine, but what's happening is that when the installer gets to the point where it loads PCMCIA drivers, it turns off the PCMCIA port, effectively cutting itself off from the CD-ROM.

I have yet to discover a workaround for this, and I'm currently having a hard time installing it myself. I have tried several times over the last year, all to no avail.

For the interested/helpful, the PCG-SR series of Vaio's have a PCMCIA CD-ROM, non-bootable USB, a phone jack, and no ethernet. Are we who are trying to make use of these wonderful tiny laptops really and truly out of luck?


-Jerry

---

### Post by gldblade on 2007-12-22
I have also been trying to get Linux onto a Sony Vaio without any success.  Anyone have ideas for what we might be able to do?  As Jerry said, CD-ROM is PCMCIA-only, there is no USB boot and no built-in ethernet.  I would love to get Linux onto this machine, but it just doesn't seem possible right now

---

### Post by tdok on 2008-01-24
I also have a Vaio (PIII 700MHz, 128mb) laptop.  It did seem to stall at 82% for a while, but then it picks up and go again after a good 30 minutes or so.  I have no network connection at all.

---

### Post by Zack McCool on 2008-01-24
Hmm.  Is it possible for you to remove the HD and install Linux on it on another machine, then reinstall it?

Or, do you know the chipset information for the PCMCIA slot?  Perhaps there is a linux driver that can be downloaded (to a floppy, maybe) and made to work?

---

### Post by james83501 on 2008-05-14
OK... I have an SR 17 with the PCMCIA DVD drive (expensive little bugger) as well. I'm a newbee to linux. However, I have wanted to put either Xubuntu, or Ubuntu on since it came out. I did _some_ research, and found others who had successfully overcome this very problem while installing an earlier version of linux. I will give you the links. They are very thorough, even with other issues that had arisen. I'll let you gurus process this for a while and see if it takes care of the many issues this little guy has. I have found a memory guy on e-bay that says technology has gotten to the point where we can replace our old memory for a couple gigs and has even specified which would work. plus a huge hard drive would be cool. Which linux do you think I should run (after you guys check out these workarounds) and should I get the larger memory and HDD. My son has Ubunto (until his windows xp crashed his whole system). I liked what I had seen and have no interest in windows any more (no dual partition BS). An e-mail (besides the post) would be nice to confirm what I need to do to get rid of Microsoft and start my linux adventure.

Following are the links:

[http://www.eyrie-productions.com/~ratinox/HTML/sonysr17.html](http://www.eyrie-productions.com/~ratinox/HTML/sonysr17.html)
[http://shallowsky.com/linux/vaiolinux.html](http://shallowsky.com/linux/vaiolinux.html)
http;//shallowsky.com/linux/vaiotricks.html

Thanks, James

---

