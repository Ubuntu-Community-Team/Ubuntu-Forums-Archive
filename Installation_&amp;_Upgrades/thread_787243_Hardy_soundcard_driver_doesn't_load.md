---
title: "Hardy soundcard driver doesn't load"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by Coert on 2008-05-08
I'm having a little problem here with my second soundcard (which I use for digital S/PDIF-out). After upgrading from Gutsy (where both cards worked fine) to Hardy, the internal SoundMax-card isn't shown anymore in the GNOME-properties. The card does show in lspci: "00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)"

It seems the driver doesn't get loaded ... I've tried modprobing the snd-intel8x0 driver. But that doesn't seem to make any difference ... :(

Anyway here's my output from ALSA Information Script:
[http://pastebin.ca/1011994]("http://pastebin.ca/1011994")

Hope someone is able to help!

---

### Post by lesergi on 2008-05-08
Do you have installed linux-restricted-modules and linux-backports-modules ?

---

### Post by Coert on 2008-05-09
Thanks for the tip. But ... installing the restricted/backports modules really screws up my nvidia-card. When I apt-get them apt forces the package 'nvidia-kernel-common' on me and kindly recompiles my kernel, really screwing up my installed nvidia-drivers that work fine (sic!). Why does it do this?? 

Furthermore, it doesn't really seem to solve my problem ... with the restricted drivers installed the intel8x0-soundcard still doesn't show up in ALSA ...

There must be an easier way to just load that pci-device into the system ...

---

