---
title: "only safe vga mode works, ok to install?"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by mistamcgoo on 2006-06-18
when boot up the dapper cd on my laptop (acer aspire 1300) it only works when i choose the "safe vga mode" at bootup (if i choose the normal boot up, the screen becomes all "messed up" at kde login). everything seems to be ok in safe vga mode, i have normal screen res and high colours. 
 
Is it Ok to install Kubuntu to my laptop, will it take the 'safe vga mode" automatically after it installs and reboot?

---

### Post by Winblowz on 2006-06-18
Yes!:D  The same thing happened to me. The X server probably wasn't detecting your video card, maybe because you have to go through extra steps to get it working. The video driver "safe mode" uses is a very basic VESA driver. For better performance, you may want to find out what the driver for your video card is and install it, after the actual installation is finished. What video card are you using?

---

### Post by mistamcgoo on 2006-06-18
this laptop has an S3 video card, i took a screenshot from kinfocenter when i had the kubuntu dapper cd loaded up, i attached it(laptop.jpg) . 

In Kubuntu breezy (my current os) i don't have any problems (i didn't use the live cd when i installed it, ) the second screenshot(breezy.jpg) is from kubuntu breezy kinfocenter

thank you for the information

---

### Post by Winblowz on 2006-06-18
Yep, you should have no problems installing Kubuntu Dapper:D  But, since you just told me that you already are using Kubuntu Breezy, why do you need to use the live cd? You could just go into your /etc/apt/sources.list and change everything to "dapper". Either way, if its working for you now, great.:cool:

---

### Post by mistamcgoo on 2006-06-18
i decided to give it a fresh install and not just update

there are native drivers supporting my pcmcia wifi nic in dapper(worked when i booted the live cd), in breezy it works only with ndiswrapper so i want to get rid of ndiswrapper (dont want conflicting drivers). next is that i have updated kde some time ago (to 3.5.2) if i want to upgrade via adept, preview shows me that 
all of kde will be removed instead of upgraded (this is a known problem, the sulotion is to install kde again after upgrade, found this info via google)
Soo i decided to just give it a fresh install, i have everything i need backed up today, and there's no other OS on the pc. Clean install will be better in the long term i think. 

again thanks for providing the information so quickly, i'm burning a new kubuntu dapper disc on my desktop pc atm, going to install in in a moment :)

---

