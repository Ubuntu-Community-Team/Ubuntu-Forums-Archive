---
title: "No video signal while trying to install Ubuntu 12.04"
date: 2012-05-19
forum: Installation &amp; Upgrades
---

### Post by modoran on 2012-05-19
Hi, I want to install Ubuntu in dual-boot with existing Windows 7 x86. The problem is after few seconds after booting from CD monitor shows "No signal" and shuts itself down. The CD seems to be read even after this ....

Tried to install in VMware and VirtualBox, it works, altough it gives me some SMbus error ...

Tried to install "inside windows", but after reboot it complains about wubildr not being found ...

Hardware configuration:
ATI HD 3850
AMD Athlon 64 X2 5200+
chipset geForce 7050m/nforce630a

On same computer older verions of Ubuntu used to work without issues (I remember having 8.04 installed quite a long time), how it became Ubuntu so bad with every version ?

---

### Post by 2F4U on 2012-05-19
Are you able to see the boot menu of the CD? If yes, press F6 and select nomodeset. Try to boot into the liveCD (Try Ubuntu).

---

### Post by modoran on 2012-05-19
No, I am not able to see the boot menu, only the splash screen.

If this option works, is any way that I can edit the ISO image permanently adding "nomodeset" option ? What tools do I need and there is a tutorial somewhere ?

The tools could be running on Linux or windows, does not matter.

---

### Post by darkod on 2012-05-19
On the first purple screen hit Esc. That will show the older style main menu.

Hit F6 for advanced options, select nomodeset.

Select Try Ubuntu from the main menu. First see if it loads the live desktop correctly.

After that you can install but you will probably need the same parameter on first boot, so that it loads once and let you install a video driver.

More details how to do it here:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

Note that for ATI another parameter that could help is radeon.modeset=1. That would need to be entered manually into the boot options when you are at the main menu.

---

### Post by modoran on 2012-05-19
Thank you for replies, the ESC trick indeed does work for me.

---

### Post by NongA_TongE on 2012-10-25
HELP!  I have a DELL XPS Desktop that was running ubuntu 10.04 with an NVIDIA GEFORCE 7900 series graphics controller.  I am trying to do a fresh install of 12.04 - with a full wipe of the drive, etc.  
I make it to various points in the install, and then the screen will flicker, and the monitor goes black with a message saying that it "can't display this resolution - optimum resolution is 1280 x 1024"  I've tried the suggestion above - selecting nomodeset, and got as far as selecting the upgrade or full install, and then it will do it again.  Any suggestions?

---

