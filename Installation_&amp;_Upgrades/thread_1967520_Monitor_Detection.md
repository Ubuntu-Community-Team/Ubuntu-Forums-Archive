---
title: "Monitor Detection"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by EchoTech on 2012-04-28
I just installed 12.04, 64-bit, clean / and swap, "old" home. Video driver is NVidia-current.

  The only thing I've noticed so far is that Gear thingy>Display shows my monitor as a laptop with no model number indicated.  The problem is that I don't have a laptop, it is a desktop with an LG W1943TB monitor.  Nvidia-Settings shows the correct information.

  I tried "Detect Displays" but nothing changed.  The correct monitor was shown in 11.10. Suggestions?

---

### Post by nizamibilal1064 on 2012-04-28
I am also using ubuntu 12.04 in my dell laptop with no dedicated graphic card, its showing display correctly  as laptop....

---

### Post by EchoTech on 2012-05-01
Bump and further information. After about 10 minutes my monitor screen goes black but the monitor doesn't go into standby mode.  The computer itself doesn't go into standby either.

 I await your superior knowledge of things Ubuntu.

---

### Post by EchoTech on 2012-05-04
Just a little nudge.

---

### Post by Beanmonster on 2012-05-07
Has anybody had any luck regarding this issue? I'm running an AMD HD 6750. Catalyst drivers show monitor but ubuntu restricts it to "Laptop"...

---

### Post by traditionalist on 2012-05-07
.............

---

### Post by EchoTech on 2012-05-10
If a nudge won't work, let's try a kick.

---

### Post by EchoTech on 2012-05-15
Bumpitty........

---

### Post by catbeef on 2012-05-16
Had a lot of fun with the 12.04 Live CD not booting, ended up with a lot of faffing around in 11.10 terminal to get 12.04 going!
But in the end it all worked out, both my monitors were detected properly even though they could only display in the mirror setting (turning it off completely corrupted the graphics on half of one monitor and the whole of the other monitor).

Decided to go ahead and install nvidia drivers 295.49.. whoa, big mistake. Monitor set to 'Laptop' (24" monitor that is certainly not part of a laptop) and stuck in horrible 640x480 resolution! yikes. Removed those nvidia drivers quicker than anything.

Back at 1680x1050, but now only my primary monitor is displaying and it still says 'Laptop' in Displays settings.

nVidia released new drivers yesterday, reluctant to be the guinea pig, but I guess it isn't hard to uninstall them if they poop up again. Lets find out!

---

### Post by choppyfireballs on 2012-05-16
[QUOTE=EchoTech;11882900]I just installed 12.04, 64-bit, clean / and swap, "old" home. Video driver is NVidia-current.

  The only thing I've noticed so far is that Gear thingy>Display shows my monitor as a laptop with no model number indicated.  The problem is that I don't have a laptop, it is a desktop with an LG W1943TB monitor.  Nvidia-Settings shows the correct information.

  I tried "Detect Displays" but nothing changed.  The correct monitor was shown in 11.10. Suggestions?[/QUOT



basically I am to assume that you did install the updated drivers after installing. If this is the case have you tried without the drivers installed. because the drivers are so new and the os hasn't been out long it could be a known issue with the nvidia drivers also what gpu are you using.

---

### Post by EchoTech on 2012-05-17
The GPU is a Gigabyte (NVidia) 9600GT.  I tried the Noveau(?) driver but It just booted to a black screen.  I also tried the version-current-updates with the same result.  The display is what it should be (1366x768).

---

### Post by choppyfireballs on 2012-05-17
> **EchoTech said:**
> The GPU is a Gigabyte (NVidia) 9600GT.  I tried the Noveau(?) driver but It just booted to a black screen.  I also tried the version-current-updates with the same result.  The display is what it should be (1366x768).

That does not answer my question when you installed did you update your drivers immediately, or did you upgrade with the old drivers.

---

### Post by EchoTech on 2012-05-18
When I updated, I checked "Additional Drivers" and it showed "version-current" as installed and active.  Unfortunately I didn't note the version number.  After I noted the display was showing "laptop" I activated "version current-updates".  This was version 295.49.  I still had a "laptop" so I tried the "noveau" driver.  This just booted to a black screen, so I went back to "version current-updates"

 Version 295.49, "version current-updates" is what I am using now.

 I see that there are a couple of other people having the same (minor) problem.

---

### Post by choppyfireballs on 2012-05-18
Have you tried uninstalling your drivers and seeing what happens. It might be when you upgraded your drivers got a little confused.

also using accelerated drivers on nvidia cards I have never had a good experience with only issues. I'm not saying they don't have a place, just that they have only ever caused me issues. I would recommend uninstalling your graphics drivers and seeing what kind of detection options you have going on. Also do you have an built in video card or is your nvidia the only form of video output that you have.

---

### Post by blknit on 2012-05-19
Same problem here with nvidia card on 12.04 .
Check bug #990492 and #567963

The problem is the lack of support of randr-1.2 in the proprietary driver.

I've just switched to nouveau driver and the monitor is detected properly.

---

### Post by EchoTech on 2012-05-19
Unfortunarely the noveau driver just boots to a black screen for me.  I get "boot from hd0,0" on the monitor and it is ever after black.

---

### Post by choppyfireballs on 2012-05-21
> **EchoTech said:**
> Unfortunarely the noveau driver just boots to a black screen for me.  I get "boot from hd0,0" on the monitor and it is ever after black.

to my knowledge noveau is not running without video drivers its runing the gpu in hardware accelerated mode.

Let's try this

if you were to unplug your graphics card would you have an onboard video card to use i.e. vga on your motherboard?

---

### Post by blknit on 2012-05-21
> **EchoTech said:**
> Unfortunarely the noveau driver just boots to a black screen for me.  I get "boot from hd0,0" on the monitor and it is ever after black.

If you are using nuoveau try to disable kms (see sticky post):

# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

---

### Post by blknit on 2012-07-19
The new Nvidia driver (302.17) has support for randr 1.2
Monitor detection should work now

---

