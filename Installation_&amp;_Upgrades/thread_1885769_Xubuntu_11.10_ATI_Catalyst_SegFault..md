---
title: "Xubuntu 11.10 ATI Catalyst SegFault."
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by LoderndenTech on 2011-11-23
I just installed Xubuntu 11.10 on my laptop today and did the usual updates and rebooted. I then installed ATI Proprietary drivers and rebooted. I opened a terminal and typed "sudo amdcccle" and entered my password, changed a few settings to increase resolution and enable dual monitors and I click apply and it crashes and says "segmentation fault". Is there a way to fix this any help would be greatly appreciated.

---

### Post by lordbinky on 2011-12-08
I have the same issue.  I tried installing the driver from the repos as well as the download from ATI without any luck.

I read somewhere that it might have something to do with xrandr, but disabling it caused more problems for me.

I have tried the latest ATI driver from ATI on Mint Debian and CrunchBang without any problems.

Did you have any luck?

---

### Post by editheraven on 2011-12-08
Post the output of this
```
dpkg --get-selections | grep xorg && dpkg --get-selections | grep fglrx
```

---

### Post by lag1980 on 2012-03-22
I am having the same issue.  Here is my output from the command above:


```
xorg						install
xorg-docs-core					install
xserver-xorg					install
xserver-xorg-core				install
xserver-xorg-input-all				install
xserver-xorg-input-evdev			install
xserver-xorg-input-mouse			install
xserver-xorg-input-synaptics			install
xserver-xorg-input-vmmouse			install
xserver-xorg-input-wacom			install
xserver-xorg-video-all				install
xserver-xorg-video-ati				install
xserver-xorg-video-cirrus			install
xserver-xorg-video-fbdev			install
xserver-xorg-video-geode			install
xserver-xorg-video-intel			install
xserver-xorg-video-mach64			install
xserver-xorg-video-mga				install
xserver-xorg-video-neomagic			install
xserver-xorg-video-nouveau			install
xserver-xorg-video-openchrome			install
xserver-xorg-video-qxl				install
xserver-xorg-video-r128				install
xserver-xorg-video-radeon			install
xserver-xorg-video-s3				install
xserver-xorg-video-savage			install
xserver-xorg-video-siliconmotion		install
xserver-xorg-video-sis				install
xserver-xorg-video-sisusb			install
xserver-xorg-video-tdfx				install
xserver-xorg-video-trident			install
xserver-xorg-video-vesa				install
xserver-xorg-video-vmware			install
fglrx						install
fglrx-amdcccle					install
fglrx-updates					deinstall
```


Any one figure this out yet?

---

