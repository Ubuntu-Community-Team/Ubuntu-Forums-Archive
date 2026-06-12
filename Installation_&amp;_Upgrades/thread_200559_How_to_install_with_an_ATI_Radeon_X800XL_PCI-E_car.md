---
title: "How to install with an ATI Radeon X800XL PCI-E card"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by ljrmorgan on 2006-06-20
I've never managed to get Ubuntu to work with my ATI Radeon X800XL card before, and I finally figured out how to, and it was actually quite easy. I thought I'd post it incase anyone else has had the same problems with this card.

**Step 1 - Download and burn the Alternative CD**

First I tried to install using the liveCD, and basically the boot screen worked, and then my screen just turned itself off after a few seconds of a flashing cursor. This also happened in safe graphics mode.

**Step 2 - Install Ubuntu**

Just do the full text install, take out the cd and reboot when prompted.

**Step 3 - Boot into recovery mode**

I didn't bother checking, but I assumed that booting into normal ubuntu wouldn't work, because X would mess up, so I just selected Recovery mode from the grub menu, and booted into that.

**Step 4 - Install the drivers and configure X**

See here, under "3D ATI Video Card Driver": [https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html")

That worked for me, I don't know how I couldn't do it before - anyway, hopefully this might help someone,

Louis

---

### Post by trongod05 on 2006-07-01
So, I went to step 4 and followed the instructions.  Since they seem to leave a few holes in the instructions such as, "How to add a restricted repository via the command line,"  and "What to do if fglrx isn't in the list of drivers to select even after you have installed the driver," do you think you might provide some instructions on how to configure this X800XL.  There doesn't seem to be a good step-by-step guide on how to do this.  There are always instructions that are left out or I guess they assume you already know what they are talking about.  I don't so could you enlighten me?

---

