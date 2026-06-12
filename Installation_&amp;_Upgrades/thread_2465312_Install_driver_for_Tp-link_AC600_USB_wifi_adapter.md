---
title: "Install driver for Tp-link AC600 USB wifi adapter"
date: 2021-07-29
forum: Installation &amp; Upgrades
---

### Post by guruao513 on 2021-07-29
Hi,

I'm new to Ubuntu. Im using 20.04 LTS. I have a TP-link AC600 usb wifi adapter that works seamlessly in Windows. But with Ubuntu, it seems additional steps are needed. can anyone please guide which is the driver that works effectively with this adapter and what is teh installation procedure?

I saw steps on few forums and tried them, it worked for sometime and now stopped working after what looks like a kernel update.

$ lsusb
Bus 002 Device 004: ID 2357:0120 TP-Link 802.11ac WLAN Adapter

Thanks

---

### Post by mikewhatever on 2021-07-29
You have to reinstall external drivers after each kernel update, and since you've done it succesfully, I am not sure what guidence is required.

---

### Post by SeijiSensei on 2021-07-29
Did you go to System Settings > Driver Manager and see if it can find the drivers? When installed via the Manager, the driver should be automatically updated along with the kernel.

---

### Post by guruao513 on 2021-07-29
But its not working effectively, gets disconnected or shows low speed time to time. Firstly, where can I find the driver that works most effectively with this device? The one I tried is from [COLOR=#2E8B57][FONT=Monaco]https://github.com/aircrack-ng/rtl8812au.git[/FONT][/COLOR]

---

### Post by guruao513 on 2021-07-29
[COLOR=#000000]System Settings > Driver Manager 

I dont see this option. How do I check in Ubuntu.[/COLOR]

---

### Post by SeijiSensei on 2021-07-30
[https://itsfoss.com/install-additional-drivers-ubuntu/](https://itsfoss.com/install-additional-drivers-ubuntu/)

Looks like it's harder on vanilla Ubuntu, but I may be wrong since I never use it.

---

### Post by MAFoElffen on 2021-07-30
What you referred to got moved in 20.04 from Settings to a tab called "additional drivers" in Software & Updates (not to be confused with the "Software Updates" app. LOL)

Here you go : [https://askubuntu.com/questions/1149117/tp-link-ac600-archer-t2u-nano-driver-for-ubuntu-18-04](https://askubuntu.com/questions/1149117/tp-link-ac600-archer-t2u-nano-driver-for-ubuntu-18-04)

That one (in that answer there) is maintained and does rebuild when the kernel updates through DKMS... Ensure that DKMS is installed so that can happen.
> This driver can be installed using [DKMS]. This is a system which will  automatically recompile and install a kernel module when a new kernel  gets installed or updated. To make use of DKMS, install the dkms package...
[https://github.com/aircrack-ng/rtl8812au]("https://github.com/aircrack-ng/rtl8812au.git")

That is what you originally built from, but... There "were changes" to the original there and the release notes say that should be re-pulled and recompiled to include those changes...

---

