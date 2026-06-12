---
title: "NVIDIA driver issue"
date: 2011-12-21
forum: Installation &amp; Upgrades
---

### Post by waldick on 2011-12-21
Noob !

I'm running 10.10, fresh install, NVIDIA GT 520 downloaded and installed the "290.xxx" NVIDIA driver.

On the proprietary drivers app it shows up as activated. When I run the NVIDIA settings app I get an error message about running "nvidia-config" 

When I run that and reboot, the xserver won't start and it goes to the command line....

When I delete the xorg.config file it will once again start normally into the desktop.

I'm using Mythbuntu and really want to offload video to the card for HD video...

when I try to enable VDPAU in Myth, I get a blank screen....


help....please...

---

### Post by BC59 on 2011-12-21
Try to reinstall the driver from Synaptic. Search for NVIDIA and find the installed driver. Choose reinstall.

---

### Post by waldick on 2011-12-21
I've been down that road...that will only give me version 260 or 270, which I tried with the same result.

When I tried a fresh install of 11.10 and checked the "install NVIDIA" during install, the machine hung on boot right after "check battery state" I believe...requiring a hard reset...

---

### Post by BC59 on 2011-12-21
Why don't you try the installation through PPA?

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```

---

### Post by dino99 on 2011-12-21
from synaptic: purge everything related to nvidia
then add xorg-edgers ppa  (or x-swat) and update
remove again xorg.conf, in case
reinstall nvidia-current, nvidia-settings (needs dkms installed first, but you still might have it)
and finally, deactivate the added ppa, and update again.

---

### Post by waldick on 2011-12-21
ok, I'll give that a try when I get home...

---

