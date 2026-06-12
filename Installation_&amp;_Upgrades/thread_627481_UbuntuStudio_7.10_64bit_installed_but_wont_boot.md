---
title: "UbuntuStudio 7.10 64bit installed but wont boot"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by strawberryjam on 2007-11-30
I have installed 64 bit version of Ubuntu Studio on my INTEL-q6600. 

All research suggested it should work fine. After install though i get a Ubuntu Studio splash screen, then it just hangs. Cant get into it. 

Any help would be appreciated.
Thank you:confused:

---

### Post by Pumalite on 2007-11-30
Post specs.

---

### Post by strawberryjam on 2007-11-30
Intel Q6600 Processor
Asus P5K SE Mobo
300Gb HDD
2Gb 667 Ram
Seagate 320Gb Hdd
Nvidia 7900Gs Graphics
Dual Viewsonic 19" LCD Displays
EMU 1212 Sound card

If I left out anything please let me know

Thank you

---

### Post by Pumalite on 2007-11-30
You should be able to boot and install a Live CD without any problems.
Try reinstalling Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by strawberryjam on 2007-11-30
I am using UbuntuStudio and it has no live option. It installs fine. When i reboot though i get the Ubuntu Studio load screen and then just goes blank.

I am thinking it might be the Video card configuration but i have no idea how to reconfigure from terminal.

---

### Post by Pumalite on 2007-11-30
Have you tried:
Ctrl+Alt+F1 to get commamd line, then:
sudo dpkg-reconfigure xserver-org

---

### Post by spoddles on 2007-11-30
I have had this problem as well...

When you get to your grub screen hit E to edit the commandline being booted - change the SPLASH to NOSPLASH...then hit B to boot...

Once you have booted you will need to change the /boot/grub/menu.lst file to include the NOSPLASH entry then reinstall grub.

Cheers,

Spoddles

---

### Post by strawberryjam on 2007-11-30
I will try them now thank you...will let you know what worked

Cheers

BTW....I cant run the ubuntu live CD either. It starts then the screen just gets distorted after the ubuntu splash screen with the scroll bar.

---

### Post by Pumalite on 2007-11-30
This could be the problem:
Dual Viewsonic 19" LCD Displays
Check Xinerama:
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by strawberryjam on 2007-11-30
I'm in!!! YAY
Thanks...reconfiguring the xserver worked.

Now i will work on installing the Nvidia drivers and configuring Dual displays

Thank you so much

---

### Post by Pumalite on 2007-11-30
You are welcome. Good luck.

---

