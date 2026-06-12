---
title: "RaLink USB rt2570 driver install"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by rid3 r3d on 2010-01-09
Hey everyone, 
I'm relatively new to Linux. Recently I bought a D-Link DWL-G122 to work alongside my built in wireless card. I found the driver that I need from here: [http://homepages.tu-darmstadt.de/~p_larbig/wlan/#rt2570]("http://homepages.tu-darmstadt.de/%7Ep_larbig/wlan/#rt2570")
I realize that I cannot install a compressed file like these, so I was wondering if someone could explain to me how to install this driver once I have extracted the files to another location.
Thanks!

---

### Post by darkod on 2010-01-10
I was trying to use the same adapter myself few months ago and if I remember correctly you don't need to install new driver at all. The problem is that ubuntu is loading wrong driver rt2500usb instead of rt2570sta. You just need to blacklist rt2500usb (it will prevent it loading) and it will use rt2570sta automatically.
To blacklist a driver open for editing:
sudo gedit /etc/modprobe.d/blacklist

In the file add a line:
blacklist rt2500usb

Save and close the file. Reboot.

You can check which driver your card is using by right clicking the networking icon in the top right of the desktop, then selecting Connection Information. It usually shows the driver used.

---

### Post by rid3 r3d on 2010-01-11
Thanks for the reply. I was able to get the device working, but I need to run a modified driver from that website. Currently the file is a tar.bz2
Im not sure how to get it to install once I have saved and extracted the files.

---

### Post by rid3 r3d on 2010-01-12
*bump*

---

