---
title: "Cannot install Ubuntu on GA-MA74GM-S2H mainboard."
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by ewh1533 on 2008-07-18
I'm trying to get unbuntu installed and ran into a roadblock from the very beginning.


I just built my system, I'm running an IDE cdrom and HD. No sata drives. 

Its the gigabyte mainboard GA-MA74GM-S2h and I'm using the onboard vga for the display.

I install Ubuntu and it never even gets to the partition screen. It loads, shows the loader with the orange bar and then goes into native linux. I'm left with a prompt and a bunch of error messages that went by too quickly to read.

When I attempted the 'try without installing' mode, it did say it couldn't detect my vga so it would only run in low rez mode, however it never ran, I was left with what seemed to be another prompt but there was no unbutu prompt there, just a blank screen I could type stuff into with no response from the kernal.

Please help, I'd like to not have to go back to windows.. if I can help it.

---

### Post by jimv on 2008-07-18
Download the Alternate CD and try that.  It doesn't use the Xserver, so it can have success where the Desktop CD fails.

---

### Post by Pumalite on 2008-07-18
What graphics (video) do you have?

---

### Post by ewh1533 on 2008-07-19
Well, I'll post this.. It say's the graphics adapter is a hybrid of two different things, an AMD chip and an ATI chip. 

> AMD 780G Chipset
The AMD 780G Chipset is the system logic of the latest AM2+ (HyperTransport 3.0) platform from AMD that enables its next generation Phenom&#8482; processors. The AMD 780G chipset integrated ATI Radeon&#8482; HD 3200-based graphics architecture. This unique combination of Integrated Graphics Processor (IGP) creates a single motherboard featuring a world-class DX10, Shader Model 4.0 graphics, ATI Avivo&#8482; Technology, and brand-new ATI Hybrid Graphics Technology and AMD UVD (Unified Video Decoder) Technology for faster and smoother game-play, a high quality video processing engine for advance quality of video and DVD playback.

What that means I don't really know. 
Edit: Windows detects it as an ATI Radeon 2100 graphics adapter 

Which alternate cd are you speaking of, one of the other distrubutions, IE kubuntu etc? Or are you speaking of a alternate installation CD for Ubuntu itself?

I downloaded the ISO file and created the boot disk. Thats what I'm running off of.

---

### Post by jimv on 2008-07-19
The "alternate" cd is a cd that will install Ubuntu without the graphical interface.  Here's the download link:

[http://ubuntu.cs.utah.edu/releases/hardy/ubuntu-8.04.1-alternate-i386.iso](http://ubuntu.cs.utah.edu/releases/hardy/ubuntu-8.04.1-alternate-i386.iso)

---

### Post by ewh1533 on 2008-07-19
> **jimv said:**
> The "alternate" cd is a cd that will install Ubuntu without the graphical interface.  Here's the download link:

[http://ubuntu.cs.utah.edu/releases/hardy/ubuntu-8.04.1-alternate-i386.iso](http://ubuntu.cs.utah.edu/releases/hardy/ubuntu-8.04.1-alternate-i386.iso)


This solved the problem, Thank you. My graphics are running, but in low rez mode. Being a total newb, I'll have to figure that out, but I'll do that in a separate thread.

---

