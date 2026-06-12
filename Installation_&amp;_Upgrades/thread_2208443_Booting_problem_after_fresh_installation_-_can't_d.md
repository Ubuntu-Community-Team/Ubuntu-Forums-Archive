---
title: "Booting problem after fresh installation - can't detect monitor resolution (I think)"
date: 2014-02-28
forum: Installation &amp; Upgrades
---

### Post by drumachine on 2014-02-28
My laptop is an Acer TravelMate 2312LM_L and I'm trying to install Ubuntu 12.04 LTS.

First of all, I tried installing 12.04 via the regular installation CD but whenever the CD loaded, the black screen with the stickman and the credit card(?...lol) at the bottom appeared, disappeared, and then the screen would flash various shades of black ad infinitum before I ever got to the installation menu.

The Alternate installation CD, however, worked perfectly. The installation menu appeared and I was able to install 12.04 without a hitch.

After successfully installing 12.04 I removed the Alternate installation disk, rebooted, and now the same problems have resurfaced, only this time, the screen goes black straight after the BIOS screen, stays black, and then starts flashing different shades of black ad infinitum again.

What should I try first to solve this problem? Any suggestions would be greatly appreciated.

---

### Post by oldfred on 2014-02-28
How much RAM, specs show 256MB as standard and that is not enough for Ubuntu with Unity. Alternative installer uses text based so it would work. 
You may be better with Lubuntu if low RAM and limited video chip.

Did you just install Ubuntu, so you have to hold shift key to get grub menu. Hold shift from BIOS until grub menu appears.

---

### Post by drumachine on 2014-02-28
I had actually upgraded the RAM to 1GB long before I installed Debian on it but the desktop manager, Gnome 3, had to run in fall-back mode (I think the graphics card is the limiting factor here).

Thanks for your suggestion to hold the shift key, that successfully brings me to the GRUB menu.

From this GRUB menu, I've managed to boot into the recovery mode where various options are presented to me. I will investigate these further. Thanks for your help.

---

### Post by drumachine on 2014-02-28
Booting into recovery mode, I'm greeted with a purple menu where I select 'failsafeX' then 'yes' and it displays an error:

> "The system is running in low-graphics mode - Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself"

I select 'ok' then 'run in low-graphics mode for just one session' where the following message appears:

> "Stand by one minute while the display restarts..."

I select 'ok' and it takes me back to the purple menu screen I was originally greeted with when I first booted into recovery mode, thus sending me in a circle!

So I go back to 'failsafeX', I'm greeted by the error again, then I select 'Reconfigure graphics' -> 'use default (generic) configuration' -> ok.

No matter how many times I press 'ok' the same choice pops up again...

So I choose 'Use your backed-up configuration (not that I have a backed-up configuration, butheywhynot), press ok, and the same choice pops up again...

So... I go back and this time select 'Exit to console log-in' aaaaaaannnnddd I'm sent back to the purple screen.

Ok, so I go to 'Drop down to root shell prompt'. I navigate to /etc/default/grub and edit this file using:

```
nano grub
```

Then I uncomment the line:
```
GRUB_GFXMODE=640x480
```
and add the line:
```
GRUB_GFXPAYLOAD_LINUX=keep
```

I save, exit then run the following commands:
```
update-grub
```
```
reboot
```

I allow it to boot automatically into the first GRUB option, and the black screen flashing remains.

I'm out of ideas, any suggestions?

---

### Post by grahammechanical on 2014-02-28
I have noticed the failsafeX problem. I consider it broken. By the release of Ubuntu 14.10 it will most definitely be broken because 14.10 will be running on MIR. There will not be an X mode.

You can try loading into Recovery Mode at the Grub boot menu. Then selecting Resume. That will try to load to a desktop without loading a proprietary video driver.

If you get to a desktop you can use Additional Drivers to experiment with available video drivers.

---

