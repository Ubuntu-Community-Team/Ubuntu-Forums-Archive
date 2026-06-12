---
title: "Ubuntu hangs on startup after install"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by jumpyjake on 2010-12-24
I recently bought a new computer and decided to put Ubuntu on my older computer which had XP on it.  After transferring my files to my new PC, I booted up my old PC using the Ubuntu Install CD.  I was able to do everything normally on the demo and everything seemed fully functional including internet.  I started the install and came upon an error reading the disc so I bought some new CD-Rs and burnt a fresh image onto the new CD. 

Everything ran smoothly and after about 20-30 minutes it prompted me to reboot to complete the installation.  So I reboot and it hangs at startup.  I shut the computer down and restarted it and it brought me to the GRUB boot screen.  No matter whether I choose a recovery boot or a normal boot, the computer will either hang shortly after making my choice, or it will boot for awhile and then the monitor will shut off and the monitor light will flicker on and off like it is not connected at all.  The computer continues running but with the monitor off I have no way of knowing if it is completing the boot cycle and booting up into Ubuntu or not.  I suspect that this may be a driver issue (it's Intel onboard graphics) but I'm not sure and I wouldn't know how to load the driver if I can't boot into the OS.

Any ideas?  I really want to run Linux on this machine because I haven't really ran Linux on any of my own computers since RedHat 5.1 so I have a lot of catching up to do.  After messing with Ubuntu on my brother's computer, I couldn't wait to install it.  


Any help would be greatly appreciated!

---

### Post by Rubi1200 on 2010-12-25
Hi and welcome to the forums :)

We need the following information please:

1. what are the _full_ specifications

2. which version of Ubuntu

Thanks.

---

### Post by jumpyjake on 2010-12-25
I was able to figure out the problem and decided to post my resolution in hopes of helping another user who may stumble across the same problem some time in the future.   I had installed a VisionTek ATI Radeon X1300 card into a PCI slot on this machine about 3 years ago and forgot about it.  After removing that and plugging the monitor into the original onboard graphics card, it booted right up in normal mode with no problems whatsoever.  

I'm now very pleased to have a dedicated Linux machine once again!

---

