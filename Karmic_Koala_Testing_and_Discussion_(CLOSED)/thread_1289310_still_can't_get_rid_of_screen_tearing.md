---
title: "still can't get rid of screen tearing"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Choad on 2009-10-12
i was hoping that the screen tearing i have suffered for the last bazillion years might be fixed... but alas no :(

got a dell 2407wfp (1920x1200@60) and a radeon hd 4770

does anyone have *any* advice for me? it's doing my nut. windows 7 is my default OS nowadays because i can't stand the ugliness of screen tearing

---

### Post by howlingmadhowie on 2009-10-12
strange. which driver are you using? i'm using a samsung syncmaster 2343BW powered by a radeon4870 using the radeon driver on ubuntu9.04 64-bit, and my display is great.

---

### Post by VMC on 2009-10-12
> **Choad said:**
> i was hoping that the screen tearing i have suffered for the last bazillion years might be fixed... but alas no :(

got a dell 2407wfp (1920x1200@60) and a radeon hd 4770

does anyone have *any* advice for me? it's doing my nut. windows 7 is my default OS nowadays because i can't stand the ugliness of screen tearing

The only way I was able to stop that was issuing nomodeset. Have you searched for and installed the latest radeon drivers.

---

### Post by Choad on 2009-10-12
using fglrx that the koala installed by default. have used every version of the catalyst available from ati's site since i got this desktop and it's always the same story.

---

### Post by Choad on 2009-10-12
> **VMC said:**
> The only way I was able to stop that was issuing nomodeset. Have you searched for and installed the latest radeon drivers.
what is nomodeset? and the koala drivers are even fresher than the ones from ati (which also didn't work)

---

### Post by kejar31 on 2009-10-12
Open compizconfig-settings-manager.

Navigate to General Options --> Display Settings.

-uncheck "Detect Refresh Rate" if the wrong refresh rate is displayed below
-make sure "Refresh Rate" is correct
-check "Sync To VBlank"

Also, check General Options --> General "Undirect Fullscreen Windows"

---

### Post by Rob2687 on 2009-10-12
I don't think the open source driver supports KMS on r600-r700 cards yet. I am running an r500 card with KMS and there are no more tears.

Kernel Modesetting is suppose to among many other things get rid of tearing. Unfortunately it's not quite done yet to make it into Karmic by default for ATI cards.

---

### Post by Choad on 2009-10-12
> **kejar31 said:**
> Open compizconfig-settings-manager.

Navigate to General Options --> Display Settings.

-uncheck "Detect Refresh Rate" if the wrong refresh rate is displayed below
-make sure "Refresh Rate" is correct
-check "Sync To VBlank"

Also, check General Options --> General "Undirect Fullscreen Windows"
done that, and more or less every combination of every likely option and been through clicking the refresh rate up 1 by 1 from 60 all the way to 100 testing at each stage and *nothing* works.

i have searched google, posted in forums, you name it. no one anywhere has anythign useful to say.

---

### Post by Choad on 2009-10-12
> **Rob2687 said:**
> I don't think the open source driver supports KMS on r600-r700 cards yet. I am running an r500 card with KMS and there are no more tears.

Kernel Modesetting is suppose to among many other things get rid of tearing. Unfortunately it's not quite done yet to make it into Karmic by default for ATI cards.
how would one go about trying it? i booted karmic adding "nomodeset" to the end of the boot line in grub, no difference.

---

### Post by Rob2687 on 2009-10-12
It makes sense that there's no difference because nomodeset disables KMS which isn't enabled by default anyways. :p The 4770 is an r700 card which won't get KMS support until kernel 2.6.32.

Unfortunately your wait will be a little bit longer but the good news is your bazillion years is probably almost over. :D

---

### Post by Choad on 2009-10-12
oh wow really? well that *is* something. you have just brightened my day.

---

### Post by Longinus00 on 2009-10-12
> **Choad said:**
> using fglrx that the koala installed by default. have used every version of the catalyst available from ati's site since i got this desktop and it's always the same story.

You will likely always get screen tearing if you use the fglrx driver. The open source driver works great without screen tearing but there is not yet 3d support. It will get 3d support, hopefully, by 2.6.32. fglrx also doesn't have KMS, and likely won't get it, which is why nomodeset didn't work.

***I should add that the reason that fglrx probably won't get getting these features is because the open source drivers are adding all these features which will make fglrx obsolete in the long run anyway.

---

### Post by tjeremiah on 2009-10-12
I created a BUG REPORT for people with Intel. The more responses the better. 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/448711](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/448711)

---

### Post by Choad on 2009-10-12
> **Longinus00 said:**
> You will likely always get screen tearing if you use the fglrx driver. The open source driver works great without screen tearing but there is not yet 3d support. It will get 3d support, hopefully, by 2.6.32. fglrx also doesn't have KMS, and likely won't get it, which is why nomodeset didn't work.

***I should add that the reason that fglrx probably won't get getting these features is because the open source drivers are adding all these features which will make fglrx obsolete in the long run anyway.
ok... open source driver it is. so you reckon if the radeon devs get their **** together we could get 3d accel on R700 cards by koala+1?

---

### Post by Rob2687 on 2009-10-12
Their "****" has been more together now than it's been for a long time. :P

---

### Post by VMC on 2009-10-12
> **tjeremiah said:**
> I created a BUG REPORT for people with Intel. The more responses the better. 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/448711](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/448711)

The OP here has ATi radeon and not Intel.

---

### Post by Longinus00 on 2009-10-13
> **Choad said:**
> ok... open source driver it is. so you reckon if the radeon devs get their **** together we could get 3d accel on R700 cards by koala+1?

3D is already in experimental phase. If you're real gutsy you can help test it.
[http://www.x.org/wiki/radeonhd%3Aexperimental_3D](http://www.x.org/wiki/radeonhd%3Aexperimental_3D)

This page gives an overview of the current state of the drivers.
[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

---

