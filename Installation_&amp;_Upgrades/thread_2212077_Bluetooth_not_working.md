---
title: "Bluetooth not working"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by rajeshwar2 on 2014-03-19
hello everyone,

I am using SONY VAIO laptop and I was installed ubuntu 12.04. In the ubuntu my Bluetooth is not working.

---

### Post by slickymaster on 2014-03-19
[LIST=1]
[*]First of all, check that your wireless devices are unlocked (no rfkill active):```
sudo rfkill list
```
[*]In case bluetooth is 'Soft blocked' you can unblock it:```
sudo rfkill unblock all
```
[*]In case bluetooth is 'Hard blocked', try to find a hardware switch on your laptop to unblock it.
[*]Then, check your kernel messages for Bluetooth related stuff:```
dmesg | grep -i bluetooth
```
[*]Does your Bluetooth driver expose an hci device?```
hcitool dev
```should list for example hci0.
[*]Check your system BIOS that Bluetooth is enabled.
[*]Is your Ubuntu kernel up to date (and did you reboot after that)?
[*]Try installing the** linux-firmware** and **linux-firmware-nonfree** packages. Your device may require loading some proprietary firmware.
[/LIST]

---

### Post by joaomfsantos on 2014-03-29
Hi,
New Ubuntu user here... The first 2 options solved my bluetooth not working on Acer Aspire v5-131. It was soft blocked.
Thank you lots

---

