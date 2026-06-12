---
title: "Ubuntu 10.10 black screen issue upon install"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by x ZackehSoul x on 2010-12-28
Ok, basically I've been wanting to dual boot Windows 7 and Ubuntu 10.10 for ages and every time I try, my screen goes black. Instead of it just failing (which was my original thought), I soon realised the screen is just REALLY dark, almost black, and you can only see it with a light shone directly at the screen. This is both during the installation and also after the installation is complete. I've tried several methods that people have suggested, none of which have worked correctly, at least as far as I can tell. I managed to get the install to be normal brightness, but as soon as I boot normally into Ubuntu it just goes dark again. Now I'm not experienced AT ALL with Ubuntu, so if somebody could step by step me what to do, it would be hugely appreciated :) So far the furthest I've gotten with it is making it boot into a command line, which is normal brightness, but obviously it's not the Ubuntu I'm wanting to use, so if anyone can expand on that to make it work properly, or give another method, I'll be hugely grateful. 

Thankyou all in advance.

Oh, and my laptop and model is the "Packard Bell EasyNote TM86-GN-005UK" with the original specifications for the laptop and no modifications

---

### Post by Rubi1200 on 2010-12-29
Hi and welcome to the forums :-)

This is a bit of a shot in the dark, but please try the following:

When the computer starts and you see the GRUB menu and the entry for Ubuntu is highlighted press "e" to edit.

Navigate with the cursor to the line that ends with > quiet splash

Remove quiet splash and type i915.modeset=1 and then "Ctrl"+"x" to boot.

Let us know if this helps and we can then take it a step further.

Thanks.

---

### Post by x ZackehSoul x on 2010-12-29
Well, something strange happened here. When I booted up, the screen was still dark, however I left it for about 30 minutes, and when I came back and moved the mouse it lit up normally. So naturally I restarted my PC to try it again, and no, nothing changed this time -.- It still stays at a dark screen. Anymore ideas?

Thanks for your help

---

### Post by Mark Phelps on 2010-12-29
I've run into the same problem repeatedly with 10.10 and have done the following to address it:
1) Boot into Ubuntu Recovery Mode in Grub
2) Select the option to repair broken packages
3) When done, and the command prompt is back, enter "startx"
4) This gets me to a normal desktop, where I do a normal shutdown.

This is fine for a few days -- when, suddenly without warning, it will do this again.

I have tried to raise this as an issue on this forum but encountered so much abuse as a result, that I had to move my thread to the Testimonials section -- to avoid the daily "bashing".

And, BTW, I have been using Ubuntu and other distros daily on my PCs for over four years now and 10.10 is the first, and ONLY, Linux distro that behaves this way.

---

### Post by Rubi1200 on 2010-12-29
I know this may not seem very helpful, but why not just go back to 10.04 if 10.10 is causing so many problems?

Stick with the LTS releases and only use the intermediate ones for testing purposes (assuming one has enough space on the drive or an extra external drive).

---

### Post by x ZackehSoul x on 2010-12-29
Ahh, I may go back to 10.04 then :) It's the first Ubuntu I've installed so I wasn't sure if it was a continuous thing with all of them :) Thankyou for the advice guys :D

---

### Post by Rubi1200 on 2010-12-30
You are more than welcome :)

LTS (Long Term Support) releases are, in my opinion, the way to go if you are looking for stability.

10.04 is supported on the Desktop until 2013.

---

