---
title: "screen turns blank after login ubuntu 12.10"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by zeemokid on 2012-10-19
After i did an update in ubuntu 12.10, i rebooted my computer and after logging in at the login screen, there was only the default background and the mouse with no dock or anything else and i couldn't do anything else. Sorry guys. I'm a beginner and really need help.

---

### Post by 2F4U on 2012-10-19
Provide more information about your hardware, graphics card and graphics driver. When you say update, do you mean an upgrade from a previous version such as 12.04, or do you mean that you only updated some packages?

---

### Post by safarin on 2012-10-19
> **zeemokid said:**
> After i did an update in ubuntu 12.10, i rebooted my computer and after logging in at the login screen, there was only the default background and the mouse with no dock or anything else and i couldn't do anything else. Sorry guys. I'm a beginner and really need help.

I think your unity-panel is failed to start up... can you pop-up your terminal by press Ctrl+Alt+T???

then try to type 
unity

---

### Post by ricardisimo on 2012-10-19
Same problem for me, [already reported]("http://ubuntuforums.org/showthread.php?t=2073192"). I selected gdm as my default login, rather than lightdm. I think that's at the heart of the problem. Can only seem to get into recovery mode by pressing SHIFT during boot up. Any clues?

---

### Post by zeemokid on 2012-10-21
alright guys thanks. i've solved the problem. apparently i made some changed to my graphics driver and that screwed it up. either way, thanks for taking your time to help me with my problem. :)

---

### Post by pantherace on 2012-10-21
> **zeemokid said:**
> alright guys thanks. i've solved the problem. apparently i made some changed to my graphics driver and that screwed it up. either way, thanks for taking your time to help me with my problem. :)

Can you elaborate please?  How did you solve it exactly?  What changes did you make and how did fix those changes?  It would be helpful to know for others with graphics problems.

---

### Post by ricardisimo on 2012-10-22
Yes, details please.

---

### Post by ben@kietzman.org on 2012-10-22
This problem sounds similar to what I faced with my wife's laptop.  Ater the upgrade to 12.10 neither the side or top menu displayed on her desktop.  It just showed an empty desktop.

That issue ended up being an incompatible video driver.  Errors associated with the fglrx driver were showing up in the /var/log/syslog.  I had to remove the incompatible fglrx driver.

sudo apt-get remove fglrx

Hope that helps.

---

### Post by mode7 on 2012-10-22
I also had issues with the fglrx driver.
I ran "sudo apt-get purge fglrx*" to revert to the open source driver, although the above command will work just fine too.

The problem is that these open-source drivers cause the fan to run on high constantly. Manually turning them or the clock speed down causes the desktop to drag around super choppily and slowly.
I have a Radeon HD 6970, for what it's worth.

Anyways, I am going to check out the AMD site. Maybe there's a beta driver or some update of some sort as opposed to the one provided via Ubuntu.

(I should've just stayed with 12.04.. my Macbook lost it's wireless on 12.10 as well, and the relevent PPA to fix it does not have a Quantal package)

Edit: I built the deb files using the installer from the AMD site (I believe Catalyst 12.10), and installed. Reboot appeared to scale the resolution down to 800x600 or 640x480, and still failed to load the panel. I don't have time to deal with this currently, so back to Precise for now!

---

