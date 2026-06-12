---
title: "Kernel 2.6.53-7 error (Maverick Meerkat)"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by arrimapirate on 2010-07-09
After updating my kernel to 2.6.35-7, it boots to a black screen. I see the Ubuntu 10.10 logo for a second then nothing. No gui and i cant access a tty terminal. For now im using the older kernel i had installed before.

Is anyone else having this problem?

---

### Post by QIII on 2010-07-09
Maverick is a development release, so you can expect things to break.

This post should probably have been in

[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

It'll probably get moved there.  Be that as it may, if you give me a few moments to upgrade my Maverick machine, I'll try to catch you there.

---

### Post by amauk on 2010-07-09
boots ok here
but for some reason, I've lost access to all NFS shares

---

### Post by QIII on 2010-07-09
After the update, I have no problems on a stand-alone machine or a VM in VirtualBox.

Can you give us some specs on your machine?

---

### Post by arrimapirate on 2010-07-09
Its an old Acer Extensa 4420 laptop.
Amd Athlon x2 processor with 2Gb of RAM and an ATI x1250 (or x1200, never been quite sure) graphics card.

I was thinking it might have been plymouth hanging when it tried to load since i have it themed, but disabling the theme didnt get it to work.

---

### Post by michaelpagz on 2010-07-09
I am having the exact same issue on the exact same machine, believe it or not. At first, after it went blank with 2.6.53-7, grub came up and I was able to continue with the previous kernel and I did so hoping for an update fix. Now grub doesn't display on boot and the screen goes right to blank. 
Probably a display issue as my wifi is enabled after a few seconds of the screen being blank. Not sure exactly how to move forward. 

Thanks for any help in advance.

---

### Post by arrimapirate on 2010-07-09
Wow thats weird. Did you make any changes to grub or add any other updates after the new kernel? 

Also, you said you could tell wifi was enabled. Does your wifi light actually work? Mine only comes on when i move the switch but that turns the light on and wifi off.

---

### Post by michaelpagz on 2010-07-11
No changes. Although I should have switched to to the previous kernel while I could. 
I didn't add anything to grub. It started grub at boot a few times and I figured it would just keep giving me the option and I would just keep using the previous kernel until I found a fix but then grub stopped displaying at boot and I was dead in the water with a blank screen from then on. 
Yes my wifi light actually turned on at the usual time that it would when gdm displayed. That leads me to believe that it is display issue. 
I just reinstalled to 10.04 since it was fresh install anyway. I will try an upgrade again soon after a little more research.

---

### Post by artfwo on 2010-07-11
I have the same issue on an ASUS F3KA laptop with RS690M [Radeon X1200 Series].

Fortunately, my laptop has another PCIE adapter (Mobility Radeon HD 2600). After switching the video card in BIOS, the system boots as expected.

---

### Post by arrimapirate on 2010-07-12
@michaelpagz: i was asking about the wifi light to see how you got it to work right. Mine has never worked the proper way under linux.

So the problem is with the drivers for the x1200 series cards then. Maybe the newer kernel doesnt handle them properly? It will hopefully be fixed in a next revision.

---

### Post by michaelpagz on 2010-07-19
> **arrimapirate said:**
> @michaelpagz: i was asking about the wifi light to see how you got it to work right. Mine has never worked the proper way under linux.

So the problem is with the drivers for the x1200 series cards then. Maybe the newer kernel doesnt handle them properly? It will hopefully be fixed in a next revision.

Ah! I honestly don't know. My wifi light worked right from my first install. I'm sorry I couldn't be of more help and sorry it took so long to respond. Haven't been on the forums in quite awhile.

---

### Post by arrimapirate on 2010-07-20
Ahh your lucky. Also, just in case you were wondering, the newest kernel (2.6.35-9) does not fix the display issue.

---

