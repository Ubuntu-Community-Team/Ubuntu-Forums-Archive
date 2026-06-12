---
title: "Suddenly nvidia-glx and hal broken?!"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by wirah on 2006-12-05
Hi,

   Just a quick post to let you guys know that one day (as with every day) I rebooted my Ubuntu Dapper 6.06 LTS machine to find that I had no working glx configuration, and no usb mouse - these had been working fine for around 9 months now, and suddenly broke.

   I examined the file /var/log/dpkg.log.1 to look for any updates which may have caused this, and found that on the 28th of November, both hal, nvidia-glx, linux-restricted-modules-common and linux-restricted-modules-`uname -r` (depending on kernel version) had all been updated, and had somehow messed up my configuration.

The steps I took to rectify this were:

sudo dpkg-reconfigure nvidia-glx
sudo dpkg-reconfigure linux-restricted-modules-common
sudo dpkg-reconfigure linux-restricted-modules-`uname -r`
sudo nvidia-glx-config-enable (or edit xorg.conf manually)

This fixed my X configuration and I was up and running again, however I still haven't fixed my mouse. It's a labtec usb mouse, comes up in lspci as a Belkin. I'm guessing it is hal which is broken, if I plug it into an internal usb slot, I get 'device wont accept id' or something similar, and if I plug it into my keyboard, it just doesn't respond. Yet here I am using it on my laptop without any problem (edgy 6.10)

Any ideas why all this happened, or how I can fix my mouse?

---

