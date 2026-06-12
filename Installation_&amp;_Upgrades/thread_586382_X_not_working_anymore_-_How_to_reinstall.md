---
title: "X not working anymore - How to reinstall?"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by pixmin on 2007-10-22
Hi there,

I'm having problems to fix my Xorg. Ubuntu boots, I see the boot screen with the "Ubuntu" and the progress bar underneath, then I believe I see what should be the GDM login screen but it's all broken. By broken, I mean I can only see maybe 5% of the screen (top right) and the rest is all either white or black, and I can't do anything but move the cursor (yes I can see the X cursor). And the keyboard doesn't seem to work either (I can set num lock on and off and I see the light on/off on my keybord, but I can't go back to the non graphical mode by doing CTRL ALT 1 or anything else).

I have tried to reconfigure Xorg server, with dpkg-reconfigure, to no result, no change at all. If I manually edit the xorg.conf file and change the driver from "ati" to "radeon" it doesn't change anything.

The only way to get access to GDM is by using the "vesa" driver. But of course I have to use a lower resolution and "ati" and "radeon" both used to work before I upgraded to 7.10

I have tried to remove GDM and re-install, but no change. I have remove xserver-xorg and re-installed it, reconfigured it, but no change after that.

Would someone be able to tell me what do I need to remove and reinstall in order to get my X back?

PS: I always used the default ATI driver that comes with Ubuntu.

Many thanks.

Gaetan.

---

### Post by Martje_001 on 2007-10-22
> **pixmin said:**
>  I have tried to reconfigure Xorg server, with dpkg-reconfigure, to no result, no change at all. 
Like this?:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by pixmin on 2007-10-22
Yes, like that.

---

### Post by pixmin on 2007-10-22
I have also tried to use the xorg.conf I was using before upgrading to 7.10 but it doesn't change anything.

---

### Post by pixmin on 2007-10-22
Not sure if this might help at all, but here are the details of my video card:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

Which used to work perfectly with the default ati driver.

---

### Post by Martje_001 on 2007-10-22
And the restricted driver?

---

### Post by pixmin on 2007-10-22
> **Martje_001 said:**
> And the restricted driver?

What about it? I haven't tried it if that's what you are asking. Do you think the restricted driver might work when the generic one doesn't? Last time I check my card wasn't supported by the restricted driver and there was no support for Linux on the ATI website for my card.

I will check the restricted driver, but I have a feeling that there is a problem somewhere else with my configuration, only I don't know where and I run out of things to install/re-configure.

Thanks :)

---

### Post by pixmin on 2007-10-22
> **Martje_001 said:**
> And the restricted driver?

Ha ha, quite funny, when I try it says:

"Your hardware does not need any restricted drivers."

Any other idea?

---

### Post by pixmin on 2007-10-22
Problem solved. I booted the computer to see if I could use the restricted drivers, and after a while I realized that the resolution was better than before, so I checked and it displayed in 1280x1024 which is the native resolution of my screen, so I checked the xorg.conf and the driver in use is "radeon" although the max resolution in that configuration file is 1024x768. I'm not sure to understand what happened here....

Funny thing though, I used to have compiz effects with ubuntu but now it says it can't enable them :/

---

### Post by EricHolmberg on 2007-10-24
Have you had any more problems with the video?

I have had very similar problems and tried all of the usual reconfigure, try restricted drivers, remove restricted drivers, etc without any luck.  I did get it to boot up correctly once and also got it to work correctly once by restarting X (using Ctrl-Alt-Backspace), but in all of those cases, after rebooting, it would go back to 700x400 (?!) for a resolution.  I have a 1280x1024 native resolution LCD.

Things tried:
[LIST]
[*][https://wiki.ubuntu.com/Bugs/AtiDriver](https://wiki.ubuntu.com/Bugs/AtiDriver)
[*][https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[/LIST]


Any pointers are greatly appreciated.  I am using AMD64 with the ATI Radeon 7000 / RV100 chipset.

---

### Post by EricHolmberg on 2007-10-24
Well, after pulling my hair out, I finally decided to create a new user and voila, everything worked correctly and I was able to properly set the display resolution to 1280x1024.  Finally!

I deleted all of the gnome settings from here:
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

Guess after 3 distribution upgrades, my settings just didn't hack it anymore!

-Eric

---

