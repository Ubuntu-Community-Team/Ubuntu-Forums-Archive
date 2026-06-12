---
title: "wifi network not detected during installation on GPD"
date: 2018-08-28
forum: Installation &amp; Upgrades
---

### Post by pkoukoulis-r on 2018-08-28
I have a GPD pocket PC. I use to run Ubuntu 16.04 on it without any major hassle, but then I upgraded to 18.04 and the orientation no longer works.
I thought I might try Lubuntu instead, since the issue is with Gnome.

While installing Lubuntu the following message appears:
"[FONT=courier new]Attempting to find an available wireless network failed.

w1p1s0 is a wireless network interface. Please enter the name (the ESSID) of the wireless
network you would like w1p1s0 to use. To connect to any available network, leave this field blank

Wireless ESSID for w1p1s0:
VM999999[/FONT]"

When using Ubuntu the Wifi is detected automatically without any issues.
All my other gadgets detect the Wifi.

Any idea why Lubuntu fails to detect and what I can do about it?

---

### Post by geofftf on 2018-08-29
You could try using a USB to Ethernet adapter during installation. After that, try going into Menu > Preferences > Additional Drivers to install drivers for your WiFi. Otherwise, go into Menu > System Tools > System Profiler & Benchmark and identify the WiFi device.

---

### Post by geofftf on 2018-08-29
Another possibility is the TP-LINK TL-WN725N. I was able to use that with Lubuntu without installing drivers. You would probably have to disable the onboard WiFi from the command line to use it.

Nonetheless, it looks like your WiFi device is recognized, and it is a connection problem. Have you tried clicking on the network icon on the Lxpanel (i.e. task bar in Windows terms)?

Alternatively, cannot you just type the network name and password when asked?

When I installed Lubuntu 18.04 using the TP-LINK device, I went into "Try Lububtu" first, and connected to WiFi using the GUI. I then double clicked the Install Lubuntu icon. I was asked to give the network name and password again, but I do not remember whether that was via a graphical or a text interface.

---

