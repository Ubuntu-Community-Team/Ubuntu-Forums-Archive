---
title: "Tricky Install question"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by gnuster on 2007-01-14
Hello there.  I'm new to Ubuntu, but not to Linux.  I installed v6.06 on my desktop and it works great!  I really like this distro! Now, in an effort to rid my home completely of Windows, I'd like to install it on an old laptop.  Here's the problem:  It's a Sony Vaio (SR33).  One of those tiny ones without a built-in CD drive.  It came with CD drive that connects using the PCMIA slot, but that's also how I connect to the network with a wireless card, so installing from a Live CD is a problem.  Is there any way I can create a full (non-live) CD/DVD set that I can use to install onto the Viao while off-line?

Also, which flavor the different *ubuntu releases would you recommend for this rather wimpy machine.  Here are the specs:

596Mhz Celeron
128MB total RAM
8MB video RAM
9GB HDD
800x600 display

I guess the bigger question is, should I even bother?  We only use the Vaio to surf the web and leave it downstairs to use when we are too lazy to walk upstairs.  Am I wasting my time here?

Any recommendations are appreciated.

Thanks,
Tom
Ann Arbor, MI

---

### Post by mkoyle on 2007-01-14
If you are really dedicated to getting rid of Windows, it might be worth it to you.  The current version of Ubuntu is 6.10 (called Edgy) (if you have a high speed internet connection you can download it and burn it to a CD from the UMN.edu servers at [http://mirror.cs.umn.edu/ubuntu-releases/edgy/ubuntu-6.10-desktop-i386.iso)](http://mirror.cs.umn.edu/ubuntu-releases/edgy/ubuntu-6.10-desktop-i386.iso)).  That link is to a live CD with a full installer that does not require any internet connection for installation.  If you would rather use that 6.06 version (I really can't think of a reason for that on a single home-use laptop), you can find that at [http://www.ubuntu.com/download)](http://www.ubuntu.com/download)).  For the actual installation, you only need a single CD.  Any packages you want later can be obtained from the internet after the installation is complete.

If you use wireless on this laptop, you might have a bit of trouble.  Search for your wireless card here to see if it is supported before you jump ;)

Good luck,

--Matthew

---

### Post by Sef on 2007-01-15
I would recommend Xubuntu.  It will do very well with your specs.  Both Ubuntu and Kubuntu are too memory instensive for your computer.

---

### Post by icefaerie on 2007-01-15
I'd also recommend Xubuntu, and since you have so little ram and might have internet connectivity issues, you should probably use the alternate Xubuntu install CD.  It's made for  installs with little RAM, and I believe you can also do networkless installs with it, so it sounds good for your computer.

Do you know what model your wireless card is?

---

### Post by gnuster on 2007-01-15
Thanks for the replies. I assumed that the Live CD relied on a live internet connection to complete the install.  My mistake.  I'll try Xubuntu and see how that goes.  The description for the alternate CD says it can be used for "upgrading" without an internet connection, so I wasn't sure about a complete install.  Regardless, I'm not too optimistic given my trials to this point.  I'm thinking the problem may be with the PCMCIA CD drive. Here's a summary of what I've tried so far:

I tried installing both Ubuntu 6.06 and 6.10, but was unsuccessful. At some point during the installation, it returns to a text screen with the message "Ok, booting the kernel" and just sits there (Same problem as "fkacct" had in this thread: [http://www.ubuntuforums.org/archive/index.php/t-186115.html)](http://www.ubuntuforums.org/archive/index.php/t-186115.html)).  Then I found out about a boot option "ide2=0x180,0x386" as explained in this thread: [http://www.shallowsky.com/linux/vaiolinux.html](http://www.shallowsky.com/linux/vaiolinux.html).  It is supposed to enable the PCMICA CD drive during the first part of the installation, but then disable it during IDE detection. With this option I got a little further, but still froze up at some point.  

Before I start looking at other versions of Linux, I'd like to exhaust all my options with the Ubuntu flavors.  Xubuntu sounds promising, but I fear the same problem will occur.  Maybe I need to copy to the HDD and install from there.  I saw a few threads on that, but it looked a bit messy. I think I have an old USB CD drive in the attic that I could try, but the bios doesn't list that as a boot option. 

Btw, the wireless network card is a Netgear PCMCIA MA401 (802.11b, 16-bit, 11Mbps)

Any other suggestions are welcome.

Thanks,
Tom

---

### Post by gnuster on 2007-01-15
Quick update... I downloaded the alternate Xubuntu and it seems to be installing fine in text mode.  Over half way there!  (fingers securely crossed ;-)

---

### Post by gnuster on 2007-01-15
Success!  Xubuntu alternate 6.06 installed with no problems.  Everything seems to be operational.  Configuring wifi was a snap.  Thanks for everyone's help!

--Tom

---

