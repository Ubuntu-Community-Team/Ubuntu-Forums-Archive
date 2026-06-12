---
title: "Ubuntu 9.10 - installing latest Nvidia driver for  GF 2 Ti"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by thewk on 2010-02-21
I have Ubuntu 9.10 installed and working with AWN. However I feel that the desktop performance is not what it should be and I thought maybe installing latest driver from Nvidia could improve this situation. I know that GeForce2 Ti is not supported by Ubuntu anymore since "Hardware Drivers" -menu does not offer any drivers.

Here what I have done:

- Downloaded latest package from Nvidia's site
- CTRL + ALT + F1 to go console
- sudo service gdm stop
- sudo sh nvidiadrivers.pkg1.run

Installer runs and says that everything is okay, but it tells me that I should update xorg.conf

- sudo service gdm start

Xserver cannot start, it complains something about glx module? I'm not Linux-expert and I have Googled my way this far but what can I do next? Or is it even possbile to install the driver for 9.10 ?

---

### Post by byStanderone on 2010-02-21
...here's what i did about nvidia:
- sudo dpkg-reconfigure -phigh xserver-xorg
- sudo nvidia-xconfig
- reboot

* after reboot check if nvidia control is present in: system>administration...click on it and adjust display preferences thru the nvidia control window

**if the nvidia control is not present, install it: sudo apt-get install nvidia-settings

NOTE: you may have to do some editing on your xorg.conf specially the resolution range of your display.

---

