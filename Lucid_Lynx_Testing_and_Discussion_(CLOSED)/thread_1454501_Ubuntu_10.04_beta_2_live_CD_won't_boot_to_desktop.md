---
title: "Ubuntu 10.04 beta 2 live CD won't boot to desktop"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sinbad#1 on 2010-04-14
Hi everyone I have been using Ubuntu for a few years now and so far i have been very satisfied with it. However recently i built myself a new rig with a radeon 5770 graphics card for which Ubuntu 9.10 does not seem to have the proper drivers so i have to grudgingly rely on windows until Ubuntu 10.04. 

Anyway downloaded, burnt and booted the latest Beta and it started up fine and i saw the new pink Ubuntu start up screen. However once it was done with that the output to my screen simply stopped and my display went into sleep mode. This has happened every time I tried it so far.

Anyone have any suggestions? 

Thanx

---

### Post by hackb0y294 on 2010-04-14
When you boot the live CD, it should show a language selection screen. Select your language and press enter. Then press F4 (for boot options), and select Safe Graphics Mode. I've tried this in 9.10, but it should work in 10.04 too (you may have to look around).

Hope this helps.

---

### Post by sinbad#1 on 2010-04-14
Yeah i can get 9.10 working but i get that stupid watermark at the bottom of the screen

---

### Post by hackb0y294 on 2010-04-14
What watermark?

---

### Post by sinbad#1 on 2010-04-14
It says my hardware isn't recognized or something by AMD. It only happens when I use the radeon 5770 if i plug my monitor to the internal graphics card (Radeon HD 3300) there's no problem

---

### Post by JediWombat on 2010-04-15
I have a XFX 5770 that I use with 9.10.  The easiest way to fix the watermark is to install the recently released drivers.  (10.3 Fixes the issue, released 3/24/2010)

Download them here.
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

One you download them,

chmod +x drivername.run
sudo ./drivername.run

where driver name is the name and location that you downloaded the drivers.

This will fix the watermark and allow you to use 9.10 while you wait for 10.04.  

**I am chomping at the bit too.  Came across this forum, b/c when I ran "update-manager -d" my system did the same thing yours did.  Splash screen, then no boot.

Anyway, hope that helps.

:)

---

### Post by sinbad#1 on 2010-04-15
Thank you! Good to hear that it' not just me with that problem. Guess I'll just go back to 9.10 until that's fixed

---

### Post by plusnplus on 2010-04-15
Hi sinbad#1,

Thats the purpose of beta version. Few or lot bugs need to be clear before it can be release.

---

### Post by sinbad#1 on 2010-04-15
I know, I'm just getting so impatient to go back to linux:p

---

### Post by AntEater on 2010-04-18
> **hackb0y294 said:**
> When you boot the live CD, it should show a language selection screen. Select your language and press enter. Then press F4 (for boot options), and select Safe Graphics Mode. I've tried this in 9.10, but it should work in 10.04 too (you may have to look around).

Hope this helps.

I have this problem with a Dell Optiplex using an Nvidia card.  There is no safe graphics mode option with the beta2 boot menus.  Is there a way of forcing the live cd to use "safe graphics" from the boot command line?

---

### Post by hackb0y294 on 2010-04-21
Try this: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/494627](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/494627)

---

