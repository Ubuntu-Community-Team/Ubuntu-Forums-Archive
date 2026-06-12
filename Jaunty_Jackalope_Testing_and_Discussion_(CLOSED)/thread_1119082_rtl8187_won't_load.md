---
title: "rtl8187 won't load"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ElVirolo on 2009-04-07
Hi everyone,

I just updated to kernel 2.6.28-11 and it turns out I can't load the module for my RTL8187B wifi card, which is rtl8187.

Here is the error message I get when I do sudo modprobe rtl8187 : 
```
WARNING: Error inserting mac80211 (/lib/modules/2.6.28-11-generic/updates/net/mac80211/mac80211.ko): Invalid module format
FATAL: Error inserting rtl8187 (/lib/modules/2.6.28-11-generic/updates/drivers/net/wireless/rtl818x/rtl8187.ko): Invalid module format

```

The thing is this driver doesn't work well at all (my connection is about the same as when I had a 56k modem, but it's even worse since most of the time it won't connect at all), so I tried installing the latest compat-wireless drivers, which didn't help much.

I tried compiling kernel 2.6.29, and the situation got a little bit better, but it's still far from perfect. I thought updating to 2.6.28-11 (official package) would improve things, but now I can't even load the module.


Many thanks in advance.

---

### Post by zevans on 2009-04-07
It's been a bit random over recent updates as to whether it works or not... but I think I just figured out why. There are multiple drivers that recognise the onboard device and some of them work, and some of 'em don't. Sometimes a driver will assume it's right for your device when it's not - so it loads, grabs the device, and prevents the proper module loading later on.

```
ze@vademecum:/lib/modules/2.6.28-11-generic$ find . -name rtl\*
./kernel/drivers/net/wireless/rtl8187.ko
./kernel/drivers/net/wireless/rtl8180.ko
./kernel/drivers/net/usb/rtl8150.ko
./kernel/drivers/staging/rtl8187se/rtl8187se.ko
```

Now unless you have edited your blacklist it's blind luck which one of these you get, as far as I can tell. I went through a phase of getting a different module loaded every day when I was following official .28 updates and trying out .29 kernels in the evening. :-)

To make things worse the chipset in many netbooks is the rtl8187se which is not quite the same thing, and needs se-specific drivers, or did until recently. There's also a bit of debate about whether the drivers in "staging" are fully supported.

Can you try 
```
$ lspci |grep -i wireless
```
I have an MSI Wind / Advent 4211 and I get:
```
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
```
and we'll try and work out which module you actually need and blacklist the others.

I currently have 2.6.29-git8 booted and I appear to have wireless working using the rtl8187se driver from staging. (I know there's a later version, it's compiling in another window as I type...)

---

### Post by bobnutfield on 2009-04-07
I don't know if this information is of any use to you, but I have that wireless chipset in my Toshiba laptop, and it is in fact an internal USB connection.  Up until the 2.6.27 (which finally supported it) it would only work with Ndiswrapper.  With 2.6.27 kernel the correct driver (the my USB connection, anyway) is the rtl8187.  If you do not find your wireless chipset with lspci, try lsusb.  If it is like mine, you will find it in this listing.

---

### Post by ElVirolo on 2009-04-08
Thank you both for replying.

My card is definitely a RTL8187B (confirmed by lsusb), as this is the driver I'm using under 2.6.29, and it works (more or less).

---

### Post by ElVirolo on 2009-04-09
I just uninstalled linux-backports-modules-2.6.28-11-generic, and I can now load the module. I can connect to the wifi network, but the Internet connection doesn't work...

---

### Post by ElVirolo on 2009-04-09
Ok, I just uninstalled linux-backports-modules-2.6.28-11-generic and I'm now able to load rtl8187 under 2.6.28-11. However, although I'm able to connect to the wifi network, the internet connection doesn't work at all. 
Guess this means I'm back to 2.6.29 and its 1MB limitation...

---

### Post by ElVirolo on 2009-04-09
Ok, I just uninstalled linux-backports-modules-2.6.28-11-generic and I'm now able to load rtl8187 under 2.6.28-11. However, although I'm able to connect to the wifi network, the internet connection doesn't work at all. 
Guess this means I'm back to 2.6.29 and its 1MB limitation...

---

### Post by ElVirolo on 2009-04-09
Ok, I just uninstalled linux-backports-modules-2.6.28-11-generic and I'm now able to load rtl8187 under 2.6.28-11. However, although I'm able to connect to the wifi network, the internet connection doesn't work at all. 
Guess this means I'm back to 2.6.29 and its 1MB limitation...

---

