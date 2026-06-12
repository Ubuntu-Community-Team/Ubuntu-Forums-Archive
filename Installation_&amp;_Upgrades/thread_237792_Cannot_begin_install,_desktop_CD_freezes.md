---
title: "Cannot begin install, desktop CD freezes"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by wired465 on 2006-08-16
I seem to have some kind of problem booting and maintaining a linux OS on my computer. It boots fine sometimes, but will eventually freeze. Sometimes I am able to start the installer, and othertimes it freezes at a brown screen. My Specs are:

Desktop CD 64-bit
AMD 3000+ 64bit
1gig mem
MB (forget the model, heh) nForce3 chipset
geforece 4 ti 4600
80gb seagate HD
linksys NIC

any help would be greatly appreciated. I also had this problem in fedora 5, and SUSE 10.1

---

### Post by jordilin on 2006-08-16
From the title it seems that you have not already installed Ubuntu. So, I would take a look at the BIOS parameters to see if there's something that may cause this. If you were using Fedora, did you take a look at system logs? If so, could you paste some relevant info?

---

### Post by arkham on 2006-08-16
Without more details of either your spec (motherboard is important to determine things like IDE controller etc.) or details of the problem (error logs etc.) it is hard to say what this might be.........

The last time I had this kind of issue, it was an issue with the IDE controller on the hard drive (I set the ide=nodma option at boot to resolve it).  The time before that, it was a RAM issue - I had to remove half the RAM to get the installer to work, afterward the RAM worked fine.  Another issue with an SATA conroller forced me to move the Hard Disk to a different port (on the second controller).

Also, try doing a text mode install or a server install rather than the graphical one, just in case that is playing a part.

Good luck!

Adam

---

### Post by wired465 on 2006-08-16
I couldn't take a look at the system logs in fedora because the system would freeze even when in failsafe commandline mode. I am currently running a memory test to see if that is the problem. My WinXP partition works fine but I cannot get a linux distro that seems to not freeze, which leads me to believe something is wrong in my box. I plan on disconnecting everything except the essentials to see if i can track down the source but any advice would be welcomed.

---

### Post by jordilin on 2006-08-16
> **wired465 said:**
> I couldn't take a look at the system logs in fedora because the system would freeze even when in failsafe commandline mode. I am currently running a memory test to see if that is the problem. My WinXP partition works fine but I cannot get a linux distro that seems to not freeze, which leads me to believe something is wrong in my box. I plan on disconnecting everything except the essentials to see if i can track down the source but any advice would be welcomed.

You could try to work with a Live Cd Linux distro for half an hour and see how it deals with your hardware

---

