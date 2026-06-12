---
title: "HP 550 Laptop WiFi problem"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by Ihsan_Cingisiz on 2010-11-15
Hello,

I installed Ubuntu on my HP 550 Laptop and i've
got a problem. I want to choose my WiFi connection
but it says that it hasn't got a firmware..
When i click on the wireless icon, this opens:

_____________________________________
**Wired Network**
  disconnected

**Wireless Networks**
  device not ready(firmware missing)
_____________________________________
  **VPN Connections**                   >

What should i do now?

Regards,
Ihsan.

---

### Post by cybergnome on 2010-11-15
Firmware is the software used by the operating system device driver to interface with and control the device.  You need to determine the name and specifications of your wireless device, particularly the chipset that it carries.  Then we can attempt to discover if it is supported by Linux or not, and what you need to download and install, if it is.

---

### Post by Ihsan_Cingisiz on 2010-11-16
> **cybergnome said:**
> Firmware is the software used by the operating system device driver to interface with and control the device.  You need to determine the name and specifications of your wireless device, particularly the chipset that it carries.  Then we can attempt to discover if it is supported by Linux or not, and what you need to download and install, if it is.

Hello,

Thanks for your repy, but i&#7743; very new to Ubuntu and don't know
whith which program i can, or how i can see the name of the device.
Could you help me out, what do i need or how can i see it?

Regards,
Ihsan.

---

### Post by rondackcpu on 2010-11-16
Ihsan:

The first thing to try is to install the package called "linux-firmware-nonfree" which is in the repository.  Simply launch Synaptic and scroll down to "linux-firmware-nonfree" and mark for installation, then click "apply".

If that doesn't solve the problem, come back for more hlp.

CRS

---

### Post by TBABill on 2010-11-16
Please type ```
lspci
``` into a terminal and post the output here. In that list is your wireless network adapter model and then users can post suggested steps to take to help get it running.

---

### Post by ausyou2000 on 2013-02-09
> **Ihsan_Cingisiz said:**
> Hello,

I installed Ubuntu on my HP 550 Laptop and i've
got a problem. I want to choose my WiFi connection
but it says that it hasn't got a firmware..
When i click on the wireless icon, this opens:

_____________________________________
**Wired Network**
  disconnected

**Wireless Networks**
  device not ready(firmware missing)
_____________________________________
  **VPN Connections**                   >

What should i do now?

Regards,
Ihsan.

Just follow these steps, it fixed mine. But I didn't have ethernet so if you don't have that download easytether on a android phone and download the .deb Nd install it... Just read the direction inside the easytether App to see how to launch it on linix.... Just self explanatory.

**_b43 - No Internet access_**

If you do not have any other means of Internet access from Ubuntu, then you will have to download the firmware from another computer with Internet access, from an existing OS on another partition, or before you install Ubuntu. You will also need the b43-fwcutter package which is usually included on the install media or can be downloaded from the official online repositories.

1. Install the b43-fwcutterpackage. This is usually located on the Ubuntu install media under /cdrom/pool/main/b/b43-fwcutter/ or you can download the binary '.deb' package by following the links on launchpad.

Double click on the package to install or in a Terminal issue the following commands:

cd /cdrom/pool/main/b/b43-fwcutter/sudo dpkg -i b43-fwcutter*

2. On a computer with Internet access, download the required firmware file:

b43legacy - [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) b43 (10.04 Lucid Lynx) - [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) 

b43 (12.04 Precise Pangolin) - [http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-5.10.56.27.3_mipsel.tar.bz2)

For the latest information on what files to download see [http://wireless.kernel.org/en/users/Drivers/b43#Other_distributions_not_mentioned_above](http://wireless.kernel.org/en/users/Drivers/b43#Other_distributions_not_mentioned_above) and [http://wireless.kernel.org/en/users/Drivers/b43/developers](http://wireless.kernel.org/en/users/Drivers/b43/developers) .

3. Copy the downloaded file to your home folder. Open a new Terminal and use b43-fwcutter to extract and install the firmware:

b43legacy

sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o

b43 (10.04 Lucid Lynx)

tar xfvj broadcom-wl-4.150.10.5.tar.bz2 sudo b43-fwcutter -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

b43 (12.04 Precise Pangolin)

tar xfvj broadcom-wl-5.10.56.27.3_mipsel.tar.bz2 sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.10.56.27.3/driver/wl_apsta/wl_prebuilt.o

4. Restart the computer or reload the b43/b43legacy module as outlined in the Switching between drivers section below (replace b43 with b43legacy where appropriate).

---

### Post by wildmanne39 on 2013-02-09
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

