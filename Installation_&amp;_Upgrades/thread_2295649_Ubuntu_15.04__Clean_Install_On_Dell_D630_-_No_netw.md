---
title: "Ubuntu 15.04  Clean Install On Dell D630 - No networking, touchpad not working"
date: 2015-09-20
forum: Installation &amp; Upgrades
---

### Post by nedim5 on 2015-09-20
As the title says I just did a clean install on a Dell D630 laptop, I was using Elementary OS Freya before, but I decided to format the drive and put Ubuntu 15.04 on it.
 
After a successful install, the laptop boots, the screen resolution is way of, networking doesn't work (meaning no wired connections and no wireless connections), there is no mouse cursor (which after a second restart did appear, only to be unresponsive - the touchpad doesn't work). 

Everything is fine when I boot from the USB stick in live mode, the resolution is correct and the quality is crisp and beautiful, Internet works, and the touchpad also.

What could be the cause? 

Appreciate your help.

Cheers, Nedim.

---

### Post by Bucky Ball on 2015-09-20
Welcome. When you are installing, are you clicking the option to install third-party proprietary software during the install or not? Do you have an ethenet cable connected during install if you are?

Radical difference, works beautifully from install media but rubbish once installed. We'll get there. :-k :)

---

### Post by nedim5 on 2015-09-20
Oh yeah, I always do that, didn't have any problems up until now with it, I will try to reinstall without checking it and get back to you. Thanks for the tip ! :D

---

### Post by Bucky Ball on 2015-09-20
Just a guess. In your case, it may be you are getting the wrong drivers or something's going wrong. From the install media it is open-source with no proprietary graphics or wireless drivers installed. 

Strange about the touchpad and other things, but we'll see where this gets us.

---

### Post by nedim5 on 2015-09-20
Just reinstalled, same thing, I also tried reinstalling once more without the "Get updates while installing" box checked, didn't work either...

---

### Post by Bucky Ball on 2015-09-20
Hmm. Shot in the dark.

Install Ubuntu. Reboot. When you get to the list of kernels after you boot the machine, highlight the one you want and hit 'e' to edit it.

Find the line that ends 'quiet splash' and make it 'quiet splash nomodeset'. Follow instructions at the bottom of the screen to save and continue. Any different?

The fact the screen resolution is right out might mean it is using a driver which is at the wrong resolution and everything's fine, just really huge and beyond the borders of the screen. The nomodeset might give us a clue.

---

### Post by nedim5 on 2015-09-20
Edited the kernel, did not work. I think it is using a bunch of wrong drivers, for the display adapter, the wireless adapter, network and touchpad.... Really frustrating. :/

---

### Post by Bucky Ball on 2015-09-20
If you install with the 'install proprietary software' option unticked it should have the same drivers you are using on the live media session. 

I'm off to bed as 3:30am here. Good luck and hopefully someone will jump in soon. If nothing in 12 hours feel free to post 'bump' or update us at anytime with progress/breakthroughs. Both will take your thread to the top of the New Posts list. 

Good luck.

---

### Post by nedim5 on 2015-09-20
Thanks a lot for your support and help, will do!

---

