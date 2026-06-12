---
title: "Help install vdpau driver"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by smallville2 on 2014-09-04
Hi all, i realy need help on install my graphic drivers i want run xbmc and i need to install the vdpau drivers for all work fine. How i install the vdpau drivers ? Im a linux newbie and i dont know how install he drivers and the vdpau. I have 2 computers one with nvidia and other with ati radeon Hd 8470D. I want to know how install ons the 2 computers.

Thx

---

### Post by slickymaster on 2014-09-04
I advise you to have a read at these:
[Getting VDPAU working through 14.04]("http://www.phoronix.com/forums/showthread.php?93947-Getting-VDPAU-working-through-14-04")
[Ubuntu Will Not Enable Open-Source VDPAU Support]("http://www.phoronix.com/scan.php?page=news_item&px=MTYwNzU")

---

### Post by SeijiSensei on 2014-09-05
VDPAU is an NVIDIA technology so it's not available for the machine with the ATI card.  Usually on NVIDIA machines I just run the command
```
sudo apt-get install nvidia-current
```
after installation.  That will install the correct proprietary NVIDIA driver and the VDPAU library.

On either machine you can also use the graphical Driver Manager. I'm not sure where that is located in xubuntu; on Kubuntu it's one of the System Settings applets.

---

### Post by grahammechanical on 2014-09-05
See this section from the MythTV wiki

[http://www.mythtv.org/wiki/VDPAU#Ubuntu_14.04](http://www.mythtv.org/wiki/VDPAU#Ubuntu_14.04)

Regards.

---

