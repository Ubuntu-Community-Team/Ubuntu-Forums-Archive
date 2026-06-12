---
title: "Wireless networking"
date: 2012-04-16
forum: Installation &amp; Upgrades
---

### Post by esnyder8 on 2012-04-16
I can't get ubuntu to recognize my wireless adaptor. I have an acer laptop and can't get the wireless working.

---

### Post by lkraemer on 2012-04-18
1. How do I know what Wifi Hardware my Computer has?

Open a Terminal Window and use these commands to get more information
on your hardware, wireless, Windows loaded drivers, and Linux drivers
that are currently blacklisted. Copy & Paste to prevent errors!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig
sudo dmesg | tail

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
If you are requesting help, post the output of each command........


lk

---

