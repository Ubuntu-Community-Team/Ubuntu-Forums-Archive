---
title: "Installing Broadcom [14e4:43a0] (rev 03) driver without internet"
date: 2022-11-02
forum: Installation &amp; Upgrades
---

### Post by mmcmonster2 on 2022-11-02
I'm trying to install Linux on a 2014 Macbook Air.  The install went fine, but wifi doesn't work.

It doesn't have an onboard ethernet port, so I can't connect to the internet to do an apt-get update, etc...

I used 'lspci -nn -d 14e4:' to figure out that the Broadcom 14e4:43a0 driver is used.  I managed to download bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu8_amd64.deb on a working installation and copied it to the laptop.

The problem is, the broadcom .deb has a lot of requirements so I can't install it.

Any ideas?  I'm ready to re-install the system, but need some way to get the wifi driver installed.

---

### Post by bobunderwood99 on 2022-11-02
Perhaps a USB  to ethernet adapter would help - e.g.

[https://www.amazon.com/UGREEN-Ethernet-Internet-Compatible-Raspberry-dp-B091TL1VQ4/dp/B091TL1VQ4/ref=dp_ob_title_ce](https://www.amazon.com/UGREEN-Ethernet-Internet-Compatible-Raspberry-dp-B091TL1VQ4/dp/B091TL1VQ4/ref=dp_ob_title_ce)

---

### Post by tea for one on 2022-11-03
> **mmcmonster2 said:**
>  I managed to download bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu8_amd64.deb on a working installation and copied it to the laptop.
If this working installation is an Ubuntu PC, you can use synaptic to generate a download script.
[https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)

Otherwise, perhaps purchase a usb wifi device.
[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

---

