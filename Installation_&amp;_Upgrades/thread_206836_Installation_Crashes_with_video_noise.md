---
title: "Installation Crashes with video noise"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by KE5DTO on 2006-06-30
I am trying to install Ubuntu 6.06 on a brand new Dell Dimension E510 desktop (3.2GHz Dual Core, 2GB ram, ATI X300 video).  I am having trouble getting the installer to work.  It seems like no matter what option I pick on the boot screen, I get to 4% on the Loading Linux Kernel status and then it locks up.  Sometimes there is video noise (strange colors like the video driver went nuts).  I imagine that I need to add some kind of boot parameter, but have no idea where to start.

Just to give you some background, I have loaded Ubuntu 5.10 on a home built Athlon XP3200+, 1GB ram, ATI Radeon 9800 Pro without a problem.  The upgrade to 6.06 went without a hitch.  But I'm still very green in terms of Ubuntu and linux in general.

Any help would be appreciated.  TIA.

---

### Post by KE5DTO on 2006-07-06
Well, no responses so far.  I'm surprised this isn't a more common issue.  After much internet searching, I tried downloading another Ubuntu image making sure that it was the 'Desktop' version.  I burned this and got the same result.  I tried using the boot options that I have seen mentioned in various threads (acpi=off, noapic, etc).  These don't seem to make a difference.

The system locks up no matter which option I choose at boot up.  Any suggestions would be appreciated.

---

### Post by domlloyd on 2006-07-07
Hi, just joined this message board and was specifically looking for the problem you also seem to be experiencing. 

I have just purchased a system with a Pentium D 2.66Ghz Dual Core Processor, with 1MB DDR2 533MHZ RAM, ATI X300 video. I had intended to install LINUX but so far every type of LINUX I have tried to install has failed, within a minute or so, with the video noise problem you are experiencing. On my machine this is immediately followed by the machine rebooting. 

I have tried to install Fedora 5, SUSE 10.1 and now Ubuntu Desktop 6.06. When I was installing Ubuntu it failed at the installing Power Management step. (I have tried installing these disks on a VMware virtual machine on a Windows Desktop so I know they work.)

I have tried changing BIOS Settings at boot time but to no avail. 

After doing some research I am wondering if LINUX is sensitive to the Dual Core or the ATI X300 video in some way?

---

### Post by bikeboy on 2006-07-07
There are sometimes issues with ATI video cards. Can you get the LiveCD to boot properly, does it need the safe graphics option to work?

---

### Post by domlloyd on 2006-07-07
I have tried the safe graphics option as well as different types of resolution. On Ubuntu I know these resolutions are working as the graphical loader screen seems to resize to the correct video size whichever one I select.

I have not tried the LiveCD but will try this and post back with success or failure. 

thanks.

---

### Post by KE5DTO on 2006-09-21
Well, here I am over 2 months later still without a solution.  The LiveCD does not work (this is the default 6.06 disc, correct?? -- there is no mention that this is the LiveCD on the download page...that creates some real confusion for newbies).

To redescribe the situation, when I hit enter to install (or even do safe mode install), the machine locks up.  I have tried command line options, but none has changed the lock up.

Sometimes I get video noise, sometimes the machine will just reboot.  On at least one occasion I saw the status bar (got to about 3 green bars) before it locked up.  Most of the time the machine just locks up hard requiring a reboot.

I have tried a host of command line options found in the F1 help with no luck.  Here are a few of the ones I can remember:
live vga=771 noapic nolapic acpi=off pci=noacpi debian-installer/framebuffer=false

Further, I pulled out the ATI x300 PCI X16 card and enabled the integrated video (something I was unaware that I had until today due to the cover Dell puts over the plug).  This made no difference whatsoever

Any help would be appreciated.

---

### Post by KE5DTO on 2006-09-25
Problem solved.  It turned out that it was not the image that I was burning or the resulting CDs (at least not directly).  It was the program I was using to burn them.

I did a quick google search looking for an program that would burn a CD from an image shortly after downloading the Ubuntu image and found "ISO Recorder" at [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm).  

This weekend I downloaded and installed CloneCD (21 day trial) on the recommendation of a friend, and this got me past the initial problems I was having with locking up immediately.  

I can now get past the point where it has uncompressed the kernel and starts it, but I am presented with a blinking cursor.  I am guessing that a combination of the previously mentioned command line arguments will help me get past that.

Anyways, I hope this helps anyone else that runs into this unfortunate situation.

---

