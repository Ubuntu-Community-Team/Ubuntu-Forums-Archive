---
title: "Workaround in Ibex for Nvidia Legacy Driver Issue"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by uniontroublemaker on 2008-10-27
Has anyone found a workaround for the nVidia "legacy" video support issue in Ibex?  I tried upgrading from Hardy to Ibex but I am stuck in the command-line prompt.  I have an ancient GeForce4 MX 420 graphics card.  The same thing came up in previous upgrades since Dapper.  Previously I was able to use sudo dpkg-reconfigure xserver-xorg and manually enter the graphics card or chose Vesa.  The release notes say that GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This did not happen when I upgraded.  Is there a way to make this happen from the command-line prompt?

---

### Post by lemming465 on 2008-10-28
Try editing /etc/X11/xorg.conf (e.g. sudo nano ...) and make sure the section with the device specification asks for the "nv" driver.  E.g. on my legacy Compaq I have:

Section "Device"
        Identifier      "nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x]"
        Boardname       "nv"
        Busid           "PCI:1:5:0"
        Driver          "nv"
        Screen  0
EndSection

---

### Post by uniontroublemaker on 2008-11-01
Thanks !  It worked.  I also had to install the nv driver:

sudo apt-get install xserver-xorg-video-nv

I am back in business.  I'll wait until Alberto Milone puts the new beta driver in the proposed repositories.

---

