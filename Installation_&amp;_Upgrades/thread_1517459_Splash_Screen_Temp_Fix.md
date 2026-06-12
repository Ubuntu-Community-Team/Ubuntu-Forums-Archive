---
title: "Splash Screen Temp Fix"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by stumay on 2010-06-25
The new splash screen would fly by in two shakes without, the dots moving left to right.
And I was looking at more blackness than purple.

So what I did was this without installing a slower uvesa v86d update.

I used that as a reference point instead.

This is what me Grub2  looks like:  /etc/default/grub



```

GRUB_DEFAULT=2
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash gfxpayload=1280x1024-24+0+0"
```

```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024-24+0+0
```

Since I'm new to this Ubuntu Kraze, I'm not 100% sure if this is good or bad.

If someone has a sure fix please let me know, since I've been scouring internet for days trying to fix the Plymouth Splash Screen thing.  Karmic and Lucid doesn't seem to interchange? is what I'm seeing at the moment.

My system:

AMD Phenom II X4 955 B.E.
MSI 785GM-E65 - AMD 785 Chipset
4GB DDR3 1333MHz 
ATI R5670 HD Radeon 1 GB DDR5 775/1010MHz
SataII Hitachi 500GB HD
SataII W.D. 320GB HD
GearHead SataII DVD RAM/Burner 

Ubuntu 10.04 LTS Lucid Lynix
21" HP Widescreen 16x9 @ 1600x900-24 
USB Mouse + Keyboard

OC'd to 3.60GHz

---

### Post by kalistona on 2010-06-25
well your machine is so perfect that i would like have the same !
try**[COLOR=Blue] launchpad[/COLOR]** for professionnal issues, i can tell you that, since few months, lucid and plymouth are bringing serious problems : it seems a testing version, unstable.
it is my point of view.

---

### Post by stumay on 2010-06-25
> **kalistona said:**
> well your machine is so perfect that i would like have the same !
try**[COLOR=Blue] launchpad[/COLOR]** for professionnal issues, i can tell you that, since few months, lucid and plymouth are bringing serious problems : it seems a testing version, unstable.
it is my point of view.

Oh, darn, if I had more dough, I send you one.

I found grub issue.

```
GRUB_DEFAULT=2
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash vga=795" 
```

AND

```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024x24 << replaced + with x and removed +0+0
```It's been fun trying to get this straightened out.  :confused: :popcorn:

---

### Post by stumay on 2010-06-25
What I get now is the Dots. trailing left to right while the disk is running fsck in the background. 

"Ubuntu"
  . . . . . 

Before fix: flash, black, login screen.

Loggout

"Ubuntu"

Whenever they get the new Kernel, which I have the 2.6.34 but isn't, it seems supported by the new ATI 10.6. I would be happy. Because water marks and no 3D is a no go.

Then before that, had a problem with install.  Black screen.

had to use:  intrid.gz "nomodest xforcevesa" -- 

Well, this is fine and dandy but I couldn't get the Grub menu on boot.  Tried the shift key but no worky.  Finally used the "ESC" key and got to the Grub menu, but this wasn't until I had ran across other help sites.  Many hours and many days.  Because don't know exactly what to look for in the search.  this is not Windows.

Then the bootsplash screen blinks in and out with different pages, purple, black, zap ding, bing bang, wap -- login screen.  

Then I ran across several pages saying to use v86d method, but this has no 3D support and acceleration is very slow.  I tried it, but the screen has this: Ubuntu 10.04 with the trailing dots, with cheap font.

Serious issues. though once they get this video driver worked out things should work without too much configuring.  

Right now working on getting the Sensors to work right. Yet, cannot get the core temp readings for each core on the CPU.  Neither the GPU. 

When will this happen?  CPU Core reading of temps, fan speeds and GPU fan speed temp, usage, so forth?  The 2.6.33 kernel reads these perfectly but not on 2.6.34 nor 2.6.32.  Even numbers bite the bullet.

I tried, 2.6.35, sensors work perfectly after installing lm-sensors, hddtemp, gkrellm

Some of the software in Ubuntu Software Center is incompatible for sensors.

Then the issue with KDE System Settings, missing applets inside.  how to get those all to show up? Is there another lib or something to install?

thanks

---

### Post by kalistona on 2010-06-25
cannot answer ! your machine is at a hight level and linux, if he needs dependancies, he will download it and install it : it is not windows !
best way is the site of your graphic card (nvidia ?)
2.35 kernel is NOT stable.
kde is missing applet ?, problem with 10 are so strange...
 well , i never saw a wap zap ding bing bang splash ! it must be very fun...
sorry enable to help you more.bye.

---

