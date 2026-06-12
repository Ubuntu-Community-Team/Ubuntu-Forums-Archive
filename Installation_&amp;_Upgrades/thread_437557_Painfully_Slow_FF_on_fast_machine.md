---
title: "Painfully Slow FF on fast machine"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by JeremyCarr on 2007-05-08
So here's the story,

I decided that my current installation of Windows XP needed to be trashed and I had two options, re-format and re-install XP, or install Ubuntu 7.04 DVD Image. So I try installing and I run into the 'legacy USB' issue preventing  Ubuntu from installing, I disable Legacy USB Support and I install Ubuntu from the Live CD mode.

So after the installation is complete I restart my computer and instead of a quick bootup, the damned OS takes something like 10-15 minutes to boot. Its obscene, and once its done booting, everything is sluggish, I feel like I'm running Windows XP on a Pentium 2, it takes 10-20 seconds to just open the Terminal!

So I'm really not sure wtf is the problem, if its my hardware:

Pentium 4 3.4 GHz 
4 gigs of RAM
Asus P4P800 E-Deluxe
ATI 9200 (128 Meg Card)
Audigy Sound Blaster 2

Other than Hardware, I'm not sure what the problem could be, I let Ubuntu do everything for me.

FYI I've never used or installed Ubuntu before, however I'm very familiar with Red Hat (Fedora Core 4&5), Gentoo Linux and CentOS (Yes I know its Red Hat, but its *not* the same as Fedora Core) and those OS's although not ran on my desktop were ran on my Laptop which has specs far less spectacular than my desktop and they have ran just as well or better than XP.

Does anyone have any idea what might be the cause?

---

### Post by hal8000 on 2007-05-09
Well, for one thing we can eliminate your motherboard and processor. I have the same Asus but my CPU is 2.8G. My boot time is now 42 seconds, but the system is not slow and comparable to other linux installs on my HD.

Start with ps auxw in a terminal, see whats running or better still try qps
You may have to install qps, so try  
sudo aptitude install qps

once installed view all processes, then click on memory colomn and cpu colomn, you may spot something that is a resource hog

pretty sure this will bew a software issue, hardware spec looks fine to me.

---

### Post by RawMustard on 2007-05-09
Jeez, it should fly on that system, something is wrong.  Do you have internet, was your nic picked up?

---

### Post by JeremyCarr on 2007-05-10
Ok, So I install QPS and I see nothing that is hogging my CPU or Memory, the highest memory usage (Resident Set Memory) is 65 Megs and thats for Firefox and total cached memory is a couple hundred megs.

So here is the weird thing.........

Ubuntu runs like complete *** BUT, when I use Remote Desktop in Ubuntu and connect to my other Windows Box, the RDP session runs just as fast as it did from Windows to Windows box, everything is fast, almost as if I was actually running the windows box directly.

The moment I switch back to ubuntu, or make the RDP session windowed, everything is shitty again.

---

