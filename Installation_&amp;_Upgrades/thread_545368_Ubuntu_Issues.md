---
title: "Ubuntu Issues"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by Geta on 2007-09-07
My motherboard on my old cpu running ubuntu went out, but the ubuntu installation remained on my hard drive. I poped in a new mobo and when I tried to run ubuntu it tells me xconf failed and gives me these errors.

No devices detected.

Fatal server error: No screens found

Being the linux newb that I am, I decide to completely reinstall ubuntu using the latest distro available. It tries to load up but it then has a bunch of errors flashing across the screen, most of them saying something along the lines of "Page file not found" and I'm finally taken to a screen that says 

"Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law. To run a command as administrator use "Sudo <command>"

My first guess was that it didn't detect the graphics card, but I've since tried a Geforce fx 5200 and it still comes up with the same errors. I'm completely stumped, anyone out there seen this before?

---

### Post by reckless2k2 on 2007-09-07
hhmmm..some one can jump in on this but you have to boot in recovery mode. can you? if not you'll need the livecd and at some point you need to 

sudo dpkg-reconfigure xserver-xorg

---

### Post by ByteJuggler on 2007-10-03
Did you get any further with this issue?  What is the specific motherboard that you've got now?  And video card?

---

