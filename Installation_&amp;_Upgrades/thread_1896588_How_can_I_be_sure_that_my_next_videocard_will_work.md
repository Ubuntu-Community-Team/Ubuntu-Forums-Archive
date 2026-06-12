---
title: "How can I be sure that my next videocard will work under Gnome-shell?"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by R Smit on 2011-12-17
I am having a lot of troubles with -I think- my videocard. I manage to install Ubuntu 11.10 (with nomodeset) and run Unity. However, with or without restricted drivers I can't run Gnome-shell.
The same problem with f.i. Mint 12, Fedora and so on.

Either the pc boots in 'fall back' mode, does not boot at all, or shows a command line and no GUI.
So after hours of trying to fix the problem, I am considering buying a new videocard.

My video:
```

roland@roland-desktopMint ~ $ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Device 0de2 (rev a1)

roland@roland-desktopMint ~ $ sudo lshw -C video
[sudo] password for roland:
  *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fa000000-faffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:e000(size=128) memory:fb000000-fb07ffff



nVidia GeForce GT420

```

---

### Post by BC59 on 2011-12-17
The simpler way to check, is through Googling. Search the name of your card and how many times is appearing to give problems and if you like to change card, search again to see if the new one is giving problems as well.

According to this forum:
[http://boardreader.com/thread/GeForce_GT_420_not_for_Linux_4vucX3fss.html](http://boardreader.com/thread/GeForce_GT_420_not_for_Linux_4vucX3fss.html)
your card is not supported in Ubuntu.

---

### Post by R Smit on 2011-12-17
Thank you; I did Google, but never found the link you sent me. I will try it.

---

### Post by dino99 on 2011-12-17
As actual kernel directly deals with X, there is no need of xorg.conf:

sudo rm /etc/X11/xorg.conf

sudo synaptic:
- remove/purge ALL the related nvidia installed packages

Your gt420 card should run smootly with the latest nvidia-current. You can get it via x-swat ppa : [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
- add it to your synaptic/third party tab
- update
- then reinstall nvidia-current & nvidia-settings (optional)

sudo reboot
sudo jockey-gtk

---

### Post by R Smit on 2011-12-24
> **BC59 said:**
> The simpler way to check, is through Googling. Search the name of your card and how many times is appearing to give problems and if you like to change card, search again to see if the new one is giving problems as well.

According to this forum:
[http://boardreader.com/thread/GeForce_GT_420_not_for_Linux_4vucX3fss.html](http://boardreader.com/thread/GeForce_GT_420_not_for_Linux_4vucX3fss.html)
your card is not supported in Ubuntu.

According to the NVidia -site the GT 420 is supported. Anyway, I bought the geforce GT 440 with the same results although I read in forums that it should work... Tried a zillion things (Ok, this is quite vague). Would I be more succesfull with a Radeon-card?

---

