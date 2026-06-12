---
title: "Weird black screen after update"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by kjh_ngisd on 2013-01-19
Hey all,
This is just weird and I was wondering if anyone else has run into it. 

I'm running 12.04.1 . And I did an "recommended update"  a couple nights ago. I applied a bunch of updates. I didn't list them since there were 20 or 30. 

Since then, this happens on every reboot:
Grub goes through ok. 
After that, you get the text screen with the status info on boot up -- ok. 
Then I hear the "log in sound" ok. 

But my screen is completely black. I can walk away and come back later and it's still black.

If i press ENTER, I hear the log in sound again and I get the normal log in screen. 

It's like the boot up process is waiting for input. Maybe it's getting an error and expecting user interaction?

It's not a big deal, I was just wondering if it was a known issue or something other people are seeing. 

I'm running a Dell 17XPS, i7 cpu, NVidia 555M Optima card, which I've got configured and is working well. 


I'm on Ubuntu 12.04.1 LTS, 3.2.0-35-generic  kernel. 

Once I complete the boot up, everything is fine. 

I can go through the updates one-by-one, but thought I'd ping people first to see if anyone else had run into this?

thanks
--kevin

---

### Post by PerLowgren on 2013-01-19
I've had precisely the same problem. Haven't figured out which package is causing the black screen, since a fresh installation of Xubuntu 12.10 works fine I've skipped the updates.

---

### Post by claven123 on 2013-01-22
Same exact thing.... grub is fine, but then black screen.  I'm not updating my laptop and waiting for the solution..

I guess it's a video driver or some issue...  I'm going to try nomodeset etc... and see if that helps.

D

---

