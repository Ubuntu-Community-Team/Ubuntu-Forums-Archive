---
title: "Installing Ubuntu problem (NEW TO UBUNTU)"
date: 2021-02-12
forum: Installation &amp; Upgrades
---

### Post by kgrcas-1 on 2021-02-12
I decided to switch to ubuntu after changing to ssd. I downloaded the 20.04.02 LTS Ubuntu and save it on my usb. I already made it into a bootable device.

So I plugged it, opened my laptop and entered the boot setting.
The boot device available is:
UEFI: VendorCoProductCode, Partition 1
Enter Setup

Choosing Enter Setup sends me to BIOS

but choosing EUFI does.. nothing. It just blank screen.

Edit: its been 20 minutes and its still a black screen.

I dont know where I went wrong.

My laptop is Asus X540UP-DM116T

---

### Post by Impavidus on 2021-02-12
> **kgrcas-1 said:**
> I downloaded the 20.04.02 LTS Ubuntu and save it on my usb. I already made it into a bootable device.
Meaning ...?

You don't first turn your usb drive into a bootable device, then save the .iso on it. To create the bootable device, you don't store the .iso in the filesystem of the usb. Instead, you write the .iso directly to the device, so that the .iso becomes the filesystem of the usb. If done correctly, the usb will become bootable.

---

### Post by guiverc on 2021-02-12
To verify the ISO, see [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)

To write the ISO to media (thumb-drive), see

[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview)
[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-macos#1-overview)
[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview)

I don't see that you mentioned if you were trying to install Ubuntu 20.04 LTS Server, or Ubuntu 20.04 LTS Desktop, but I'll also provide

[https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/tutorial-install-ubuntu-desktop#1-overview)

---

### Post by kgrcas-1 on 2021-02-12
I used ISO 2 USB app and burned the download file in the usb. Is that not enough to make it into a bootable device?

---

### Post by guiverc on 2021-02-12
I for one, don't know the ISO 2 USB app, nor what types of ISO files it can cope with.  

Can it handle the type of ISO that is used by Ubuntu ISOs? or was it written for a specific purpose (a particular ISO, eg. a quick scan online implies to me it  was designed to write microsoft ISOs to thumb-drives, which are not the same type as that used by Ubuntu).

There are different types of ISOs, the Ubuntu tutorial links I provided will work with all Ubuntu, and *flavors* of Ubuntu ISOs, providing links for windows, mac os, & of course Ubuntu (or other GNU/Linux).

---

### Post by oldfred on 2021-02-12
Issues often common across similar models. Bigger difference if Intel or AMD based.
Some older threads, but may be same issues.

Asus x541ua Update of UEFI & SSD firmware solved issues
[https://ubuntuforums.org/showthread.php?t=2414431](https://ubuntuforums.org/showthread.php?t=2414431)
[https://ubuntuforums.org/showthread.php?t=2420860](https://ubuntuforums.org/showthread.php?t=2420860)
Asus X541UV [SOLVED] How to partition my ssd in order to install ubuntu 17.10 / 16.04.4
[https://ubuntuforums.org/showthread.php?t=2392861](https://ubuntuforums.org/showthread.php?t=2392861)

If you have nVidia, you need safeboot & install of proprietary (nVidia) driver. The old way was to use nomodeset to boot installer & also then when booting install until you installed nVidia driver from Ubuntu repository.

---

