---
title: "Ubuntu 11.04 64 Bit Reboot After Install Issue"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by alarinn on 2011-07-09
I've looked at all of the threads about issues like this but none of them helped.  My system is:
 
Abit AN8 32X
AMD 64 X4400 Proc
2GB RAM
3 x 1TB HDD SATA
HP 22X DVD Burner
nVidia 7200 video card
 
I installed Ubuntu but when I reboot I can see it trying to read from the CD first (since it's 1st in my boot order), but then it hangs after that.  I've removed all of my HDD but 1 and it should boot into it but it doesn't.  I see a blinking cursor at the bottom of the boot sequence and then nothing else happens.  If I use the LiveCD and take a look at that volume, the data is all there.
 
What should I look for next?

---

### Post by alarinn on 2011-07-10
OK, I installed the 32 bit version and I was able to get in but a required driver alert popped up on the video card to install the recommended drivers which I did.  Once I return, I login and then nothing works on the desktop.  I can move the cursor around, but can do nada.  Ubuntu 9 was much easier to install than 11 has been.  Seems 11 took 5 steps back.  
 
FYI, this same machine had no issues using Ubuntu 11.04 32/64 bit in VirtualBox in Windows 7.

---

### Post by Quackers on 2011-07-10
What happens if you reboot, rather than logging out?

---

### Post by alarinn on 2011-07-10
Well what it was doing is go through the BIOS startup and then try to read from the CD then HDD and then nothing after that but a blinking cursor.
 
But what I did was went out to BestBuy and buy a new dvd burner.  This machine is somewhat new (mobo and cpu are kind of old), but the dvd drive is from a Dell XPS I bought back in 1998.  How I went down this road was to download the WD diagnostic program and scanned all of my HDDs and none came back with errors.  I wrote zeroes over each drive and then installed Ubuntu 64 and it worked.
 
The only issue I found was updating the nVidia drivers, which I got working after a few tweaks I found on the forum.  So far, so good.
 
Short story long, it was the dvd reader.

---

### Post by Quackers on 2011-07-10
Oh well, you found some things out then :-)
Glad things are working now!

---

