---
title: "Boot from CD then switch to USB Question"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by Bill Z on 2010-05-15
Want to build USB bootable drives and use them on some older IBM T21 laptops.  The BIOS on these T21s don’t boot from USB and the USB is only USB1.0 but they are what I have.
   
  I was thinking that I could have basic exe or crenel on a CD that would have enough information that would then boot from the USB and not need to go back to the CD after boot.  However, I don’t have the knowledge or how to.
   
  I am starting from scratch here and have no preferences except to use this older hardware.
   
  Someone please help me here and provide the necessary steps and pointers to needed software. 



My searches only came up with how to build USB or CD boot, not one from the other.

---

### Post by CPPCrispy on 2010-05-15
Plop boot manager does this. All you have to do is put it on a CD and then boot from it. Once it boots there is a choice for USB.

[http://www.plop.at/en/home.html]("http://www.plop.at/en/home.html")

---

### Post by Bill Z on 2010-05-17
Thanks for the links and information.  This weekend, I spent most of Sunday (after church) messing with this.  First one thing and then another.
   
  Building the jump drive took some effort.  More than first realized.  I tried using some older jump drives with no success.  512Mb seem to be too small.  
   
  The PLoP Boot worked right off.  No problems with this step.
   
  I want to suggest to all,  to reconsider this path; if the old machine they want to boot the USB jump drive from is a USB 1.0 or 1.1.  After you do all of this work, the response speed isn&#8217;t acceptable.  The CD ROM is faster (but you can&#8217;t save stuff to a ROM).  
   
  I tried the Jump   Drive I made on a Dell Latitude C640 and on the IBM T21.  The Dell worked but took 2 hours to load the OS and for ever to wait on the screens to change.  The IBM never worked.
   
  One last thing.  I tried a PCMCIA card that had USB 2.0 connections in it.  But PLoP didn&#8217;t recognize it and wouldn&#8217;t boot the Jump Drive in it.  This would have been nice if it worked.

---

### Post by Bill Z on 2010-06-16
Just an update for any interested.  I tried my USB bootable Ubuntu on a brand new Toshiba laptop with an Intel Core i7 chip and HD screen.  It started to boot but the screen went blank.  I figured that there were no drivers for the new HD screen.  
   
  Later I tried a 3 year old Dell and it booted up fast and ran as expected.  There was a problem with the wireless device but nothing that couldn’t be fixed quickly.  Everything else seemed to work comfortably fast.

---

