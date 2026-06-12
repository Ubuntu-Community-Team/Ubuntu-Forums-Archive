---
title: "Can't install 14.04, possible graphics issue prevents me from seeing installer"
date: 2014-05-11
forum: Installation &amp; Upgrades
---

### Post by dekaru01 on 2014-05-11
I'm trying to install 14.04 64-bit on my desktop (Core 2 Duo E6550@2.33 GHz, 4 GB of RAM, Nvidia GeForce GT240 graphics). I boot from the DVD (which I've used earlier today to install Ubuntu on another machine without issues), the Ubuntu logo hangs around on screen for a couple of minutes or so, and then I see what you can see in the image I've uploaded to my Dropbox here:

[https://www.dropbox.com/s/qhodecskx96lmhy/20140511_220656.jpg](https://www.dropbox.com/s/qhodecskx96lmhy/20140511_220656.jpg)

The strange thing is that I see the exact same thing upon trying to run GParted-Live from a DVD with default settings. 

I've waited 10 minutes on this "screen", and nothing changes. What gives?

I've installed Ubuntu (various versions) a few times so far over the years, and I've never encountered anything like this. It looks like a graphics issue to me, but I have no clue what to do. 
Any help would be very much appreciated. Thanks.

---

### Post by kc1di on 2014-05-11
Hi dekaru01,

Nvidia card can be a little fussy. 

you need to boot in the nomodeset mode.  you can do that by holding down the left shift key as ubuntu begins to boot.  As screen will come up and at the bottom of it will be a number of F key options choose F6 from the list click on nomodeset hit esc and then enter. see if it boot for you, your resolution will not be right, you'll have to add the correct video driver after you install ubuntu. good luck.

---

### Post by dekaru01 on 2014-05-13
"nomodeset" did the trick for me. Thank you very much!

---

### Post by kc1di on 2014-05-14
Your Welcome , Enjoy

---

### Post by p.callan on 2014-05-14
dekaru01:
Did those F key options appear for you? I'm holding shift but I end up at the login screen as usual.

---

### Post by kc1di on 2014-05-14
Hi P.callan,

On some machines you have to have the right timing  try hitting the left shift key repeatedly, as the machine starts to boot. see if it works.
If that does not work[ here's the ubuntu doc]("https://help.ubuntu.com/community/BootOptions") that talks about the advance boot page.

---

