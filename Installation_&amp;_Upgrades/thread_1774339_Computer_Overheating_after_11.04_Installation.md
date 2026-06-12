---
title: "Computer Overheating after 11.04 Installation"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by ezm on 2011-06-03
Hi All, My computer is running really really hot after the installation of 11.10.  If the thing is just sitting idle the core temperatures are up in the 70C range.  I have a HP G62t-250 with a Itel i3 dual core cpu and and ATI Mobility Radeon Graphics card.  I suspect that this is a Ubuntu problem because when I boot into Windows 7 (the machine is a dual-boot machine) the temperatures eventually drop at idle to between 40-50C.  Also the system monitor is reporting that the cpu usage, even at idle, is about 28-30%  And I'm using gkrellm to get the temperature, and it shows that some of the CPUs are running consistently at 50-80% with just gkrellm running and nothing else.  Any ideas??

Any help would be much appreciated.  I don't want to fry this computer!!

---

### Post by ezm on 2011-06-03
I wonder could this be a product of using the 64 bit Ubuntu version?

---

### Post by Skaperen on 2011-06-03
Do you see the same issue running from the 11.04 LiveCD?  If so, then you have the opportunity to compare amd64 vs. i386, and 11.04 vs 10.10 via LiveCD so you won't need to do more installs.

I suspect the Unity interface.  When I run 11.04 in a virtual machine, it tells me my video card is not powerful enough, and drops back to plain Gnome.  10.10 in a virtual machine works the same as on real hardware.  So it seems Unity is using more advanced features of the video card and possibly using them heavily (lots of shading, tiling, etc).  Is it the GPU or video card that is heating up?

But also check what processes are running with the top command, especially if the CPU is what is heating up.

Are you comfortable switching over to text mode with Ctrl+Alt+F1?  To get back to the graphical display, usually press Ctrl+Alt+F7 or Ctrl+Alt+F8 or such.  See if things cool down while in text mode.

Or maybe this is some laptop that has an issue with poor thermal surfacing on the CPU as many have by various manufacturers.  Is the fan working?  Due to the compact air spaces inside a laptop, cooling is harder to do.

---

### Post by ezm on 2011-06-05
I think I may have figured it out.  I did in fact try switching to text mode, but at first that wasn't working.  I was getting this strange error EXT3_fs error about "deleted inodes."  It prevented me from logging in.  The partition in question was my home directory, which I've set up as a separate partition.  I decided to reformat the partition and after I did the overheating stopped.  Also the CPU activity at idle dropped way down.  So I don't know exactly what was going on, but it seems like it may have had something to do with the partition file system error.

---

### Post by Skaperen on 2011-06-06
> **ezm said:**
> I think I may have figured it out.  I did in fact try switching to text mode, but at first that wasn't working.  I was getting this strange error EXT3_fs error about "deleted inodes."  It prevented me from logging in.  The partition in question was my home directory, which I've set up as a separate partition.  I decided to reformat the partition and after I did the overheating stopped.  Also the CPU activity at idle dropped way down.  So I don't know exactly what was going on, but it seems like it may have had something to do with the partition file system error.
I wonder if corruption in the filesystem's infrastructure could have caused programs or kernel threads to be running astray.

---

