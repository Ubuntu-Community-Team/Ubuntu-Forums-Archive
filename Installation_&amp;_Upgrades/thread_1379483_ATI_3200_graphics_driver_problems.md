---
title: "ATI 3200 graphics driver problems"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by new_tew_this on 2010-01-12
I Just installed Kubuntu 9.10 64-bit on a new hd in my machine. It originally came with Windows 64-bit Vista but the HD failed and I hate windows. I am having a problem getting the graphics driver for my card to install. I have tried several different posts and followed the instructions but can't seem to get it right. Can anyone help? Does Ubuntu 64 bit have fewer problems than Kubuntu? I think I like the gnome environment better.

---

### Post by adam814 on 2010-01-12
If you like the GNOME environment better you should use it (you can install it in Kubuntu with "sudo apt-get install ubuntu-desktop").

It wouldn't have any less graphics problems than Kubuntu as it would use the same kernel/drivers/xorg setup.

I have Mobility Radeon HD 3400 and I had no luck whatsoever either with Catalyst from the ATI site or the version in jockey.  I finally ended up sticking with the open-source radeon driver.  Just make sure you uninstall the ATI driver first as it overwrites the MESA GL libraries and breaks radeon and radeonhd.  Then just change any references to fglrx in your "/etc/X11/xorg.conf" to ati.

---

