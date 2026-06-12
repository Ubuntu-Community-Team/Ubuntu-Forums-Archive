---
title: "Installation packages missing"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by prajwal82 on 2011-04-17
I'm trying to upgrade from Ubuntu 10.10 64 bit version to 11.04. I followed the steps mentioned in the website. At the end of upgrade, I got an error message saying 'failed to fetch the following files'.

[http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.6.0-1ubuntu12_amd64.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.6.0-1ubuntu12_amd64.deb)

[http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-synaptics/xserver-xorg-input-synaptics_1.3.99+git20110116.0e27ce3a-0ubuntu12_amd64.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-input-synaptics/xserver-xorg-input-synaptics_1.3.99+git20110116.0e27ce3a-0ubuntu12_amd64.deb)

[http://in.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.2.159.1ubuntu1_amd64.deb](http://in.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.2.159.1ubuntu1_amd64.deb)

[http://in.archive.ubuntu.com/ubuntu/pool/main/l/lintian/lintian_2.5.0~rc2ubuntu3_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/l/lintian/lintian_2.5.0~rc2ubuntu3_all.deb)

The above files are missing from the server, although they are available in us.archive.ubuntu.com 

Is it possible that I manually download these files and complete the upgrade?

---

### Post by mörgæs on 2011-04-17
Hi, welcome to the fora.

Best is to select another mirror for downloading. After that, remember to reload the package list.

---

### Post by prajwal82 on 2011-04-17
Thanks. I used the update manager to do the upgrade. How do I select another mirror? Almost 99% of the upgrade steps are done. Do I have to start from the beginning?

P.S: I'm new to Ubuntu

---

### Post by prajwal82 on 2011-04-17
I had to change the settings in update manager to point to the main server. That worked.

---

