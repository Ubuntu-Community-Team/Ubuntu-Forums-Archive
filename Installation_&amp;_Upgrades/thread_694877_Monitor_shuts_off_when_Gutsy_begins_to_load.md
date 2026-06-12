---
title: "Monitor shuts off when Gutsy begins to load"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by larcar on 2008-02-12
I'm a new Linux user and recently installed Gutsy on my laptop.  There were some problems (sound and video) but the things are working pretty good now thanks to ideas I found in the forum.  Now I'm trying to install it on an older desktop.  

The livecd stalls once it reaches the gold (or yellow?) screen.  There is a message early on about the BIOS being out of date.  I've followed some suggestions in the forum about using the Alternate CD.  First time it wouldn't install the grub.  Second time it evidently did.  However, after the installation completed and the computer reboots the monitor shuts off.  Every time I attempt to boot the message "grub is loading" appears followed by the message about the old BIOS and ACPI.  Then it says "loading, please wait" and that's when the monitor shuts down.

So, the problem is that I can't even get into Ubuntu to make any of the adjustments mentioned in other threads.  Any ideas anyone?  Thanks!

BTW, this is my first time posting on the forum.  I hope I'm doing it right.  If there's a problem feel free to let me know.  :)  I'm not even sure if this is the best forum for this post.  I chose it because of the installation problems I'm having on the old desktop.

---

### Post by ajgreeny on 2008-02-12
Sounds like a video card problem to me but I'm no expert in things of this type.  What card do you have in your machine?  Is there any setting in the BIOS you can change related to the video card or ACPI?  If so, go through the options one by one and you may just be lucky and get one that works.

---

### Post by larcar on 2008-02-12
To be honest I don't remember what video card the machine has.  I formatted the hard drive so my windows 98 is not on the computer any more.  As a result I can't boot anything right now to check.  Tomorrow morning I'll open the case and take a look at the card and I'll look also at the bios to see if there's any settings about the video or ACPI that I can tweek.  Thanks for the ideas.  I'll post back tomorrow with what I find.

---

### Post by larcar on 2008-02-13
Here's some info on the system.

Pentium II - MMX
CPU at 300 MHz
P6LX-A motherboard
128 MB RAM
Video card: NVIDIA GeFORCE 2 MX

I didn't see anything in BIOS that would help but tried a couple of things without any positive results.

However, I did notice that when the grub starts loading that I have about 2 seconds to press ESC to go to the grub menu which doesn't appear on it's own.  In the menu I've tried editing some lines according to suggestions I've seen on the forum about the monitor turning off.  For example I've added "acpi=force" to the kernal line but it doesn't seem to make any difference whatsoever.  The monitor shuts down right after the grub is done, hence when the kernal starts loading (I guess).  The best results I get are when I follow one suggestion I've seen and remove the "quiet" from the kernal line and change the "splash" to "nosplash".  Then it proceeds with loading the kernal, drivers, etc. and the monitor doesn't shut down until it's ready to display the boot screen (yellow screen).

From what I've seen from others while the system is small (300MHz and 128 RAM) it should be able to handle ubuntu.  Any help would be greatly appreciated.

---

### Post by larcar on 2008-02-13
Just some update notes.

I changed the "hiddenmenu" setting in the menu.lst so now the grub menu does appear.

I've tried all the different vga settings (791, 792, etc.) but the results are always the same.  I'm now downloading Xubuntu 7.04 to see if that works for me.  I've tried Ubuntu Gusty and Feisty.

What I don't know is if the ACPI situation is causing the monitor to shut off or if it is something else.  Can someone answer that for me?  Thanks.

Should I move this thread to a different forum, and if so, how?

---

### Post by larcar on 2008-02-13
I tried the alternate CD of Xubuntu 7.04 and it installed correctly.  That makes me happy.:)  It works fine with my video card.  I wonder what the difference is between it and Ubuntu as far as how it handles the video.

I still welcome any comments and ideas.  I debating whether to leave it as it is or attempt the install for low memory system instructions found on [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
Any suggestions?

---

### Post by ajgreeny on 2008-02-13
Your problem is undoubtedly 128 MB ram.  You need at least 256 for ubuntu, better with 512.  128 is just not enough for gnome, but obviously is for xubuntu.  So--

get more ram or stick with xubuntu.

---

### Post by larcar on 2008-02-14
I had not realized about the memory requirements before but found them yesterday.  So I guess you're right about that being the cause of the problem.  Thanks for replying.  I'm having other issues with that older system that I hope I can work out but Xubuntu itself is running smoothly.  I'm hoping to use linux more and more.  It's just the problems with getting it working with all the hardware that's a pain.  After that it runs nicely.

---

