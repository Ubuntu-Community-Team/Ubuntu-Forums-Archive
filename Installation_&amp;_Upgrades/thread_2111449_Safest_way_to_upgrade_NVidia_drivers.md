---
title: "Safest way to upgrade NVidia drivers"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by Dural on 2013-02-01
I have a HP HDX16 1140-US and I am running Ubuntu 12.04 64-bit on it. Its video card is a Nvidia 9600M GT. I want to update to the latest driver ([http://www.nvidia.com/object/linux-display-amd64-313.18-driver.html](http://www.nvidia.com/object/linux-display-amd64-313.18-driver.html)). However, I'm not sure of the safest way to do this without running into the problems I've heard about when it comes to update the NVidia graphics driver (ex. no GUI, blank screen, locked wrong resolution). I added the PPA x-swat but it seems that to get the latest version of the drivers I need to use the xorg-edgers PPA. My computer works fine using the current experimental drivers (304.48), but I would like to get the latest version so that I don't miss out on any important improvements (ex. power saving features). Is it worth it or should I just wait a bit more?

---

### Post by dino99 on 2013-02-02
[http://ubuntuguide.net/install-latest-nvidia-graphics-drivers-in-ubuntu-linux](http://ubuntuguide.net/install-latest-nvidia-graphics-drivers-in-ubuntu-linux)

---

### Post by haqking on 2013-02-02
Safest way is to have backups or more specifically a clone.

Then you can try any method you like until it works without worrying.

Personally I have a PPA and do it from apt-get upgrade, if there is an issue then I clone back my backup and do it manually with the download from nvidia and run the .run file from console.

---

