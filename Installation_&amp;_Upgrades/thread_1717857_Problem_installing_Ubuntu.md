---
title: "Problem installing Ubuntu"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by mediabob on 2011-03-30
Hi, I downloaded the 32bit Desktop version of Ubuntu 10.10 from the website and burned the ISO to a DVD and I want to install it on a PC.

Now my understanding is that when you boot from the DVD it should boot a Live CD version of Ubuntu and give you the option to try it or install it correct?

When it boots from the DVD it takes me to a desktop with a taskbar at the top with what looks like a power button in the upper right corner and a speaker icon next to it... and that's it. It does nothing else. I don't get the splash screen, and while I do have a mouse it doesn't doe anything, and clicking on the "power" button does nothing. I just have to shut the PC off. 

Any ideas?

Thanks!

---

### Post by Rubi1200 on 2011-03-30
Hi and welcome to the forums :-)

Did you burn at the lowest possible speed?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Did you check the integrity?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

What graphics card do you have and how much RAM?

Don't forget you are running from an optical drive; it will be slower and take longer for things to load than a normal install.

---

### Post by mediabob on 2011-03-30
Hi, thanks for your response

The PC has a Nvidia GeForce 4 MX4000 and has 32MB VRAM and has 2 GB of RAM

While waiting for a response I burned the image again just to be sure on a CD instead of a DVD at 2X and it still did not work, got a similar result except the Power/Speaker Icons are now on the left and I have NO mouse at all.

Also, on the first one I burned it looked like the taskbar had a gradient applied to it, on the second copy it was flat with a Win98 ish  look to it.

I figured from an optical drive it was just slow, so I let it set for almost 45 min with no change.

I did check the integrity with the MD5SUM and it was OK

I should add this PC currently has Windows 7 installed on it, and I want to install OVER Win7 not dual boot.

---

### Post by Rubi1200 on 2011-03-30
As you boot the DVD, try setting the nomodeset option and see if it makes a difference:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by mediabob on 2011-03-30
Thank you very much that solved my problem!

---

### Post by Rubi1200 on 2011-03-31
No problem, you are more than welcome :)

---

