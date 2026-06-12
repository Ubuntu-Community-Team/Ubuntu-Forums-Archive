---
title: "Cannot install Feisty Fawn 7.04 on a HP d530 with Intel 865 on board graphic"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by mario.rimann on 2007-04-30
Hi

I've used an HP d530 Small Form Factor box as local fileserver for the last 2 years with different releases of Ubuntu installed on it (no graphical user interface!) and everything worked well.

Now I want to completely re-install that box with the latest release (7.04) - but my tries were without success: As soon as the graphical user interface is beeing loaded, the screen changes to black - and stays black. Also after >30min nothing happens. I tried different stuff at the boot prompt, without success.

On board this box has an Intel 865 chipset - as of the hardware compatibility list, this should be recognized automatically and beeing used with the Intel 810 driver without problems.

Is there a possibility to get that system to run without having to buy a new graphic card?

Cheers,
Mario

---

### Post by hal8000 on 2007-04-30
Have you tried installing from the alternate CD? You have a choice to install in text mode, after installing you may be able to alter your resolution with
sudo dpkg-reconfigure xserver-xorg

---

### Post by harry12 on 2007-04-30
.
 I had problems with my HP laptop (dv4100 series) and ended up using Darik's 'Boot and Nuke' on the drive.  It was a drive problem (failed the BIOS drive test) so I wiped the drive. The fresh install of Feisty Fawn went smoothly, wireless worked 'out-of-the-box'; anything I've tried so far has worked great.

 What I'm suggesting is: Wipe the drive - reload.

                            harry12

---

### Post by mario.rimann on 2007-05-01
> **hal8000 said:**
> Have you tried installing from the alternate CD? You have a choice to install in text mode, after installing you may be able to alter your resolution with
sudo dpkg-reconfigure xserver-xorg

That was a great hint! I tried it and it worked out. During the installation, the screen looked very strange and it seemed that it broke down - but after >10min it continued, ...

Thanks for the help!

---

