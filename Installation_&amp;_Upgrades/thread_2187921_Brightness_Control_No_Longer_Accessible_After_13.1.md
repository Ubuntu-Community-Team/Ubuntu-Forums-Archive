---
title: "Brightness Control No Longer Accessible After 13.10 Upgrade"
date: 2013-11-14
forum: Installation &amp; Upgrades
---

### Post by kylakemike on 2013-11-14
Greetings Brethren,

After the 13.10 clean install I no longer have a brightness slider with which to increase my laptops display. Anyone else experiencing this problem? Any thoughts or ideas? Any and all help greatly appreciated.

---

### Post by Toz on 2013-11-14
Lets get some detailed information about your system. Can you open a terminal window, type in the following commands, and post back the results:

1. Your current kernel boot line:
```
cat /proc/cmdline
```

2. Info about your video card(s):
```
lspci -k | grep -iA2 VGA
```

3. Your current backlight interfaces and their values:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

4. Your dmesg log file:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

5. Your Xorg log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

6. Your kernel modules:
```
lsmod
```


Note: if you get a message about pastebinit not being installed, you can install it via:
```
sudo apt-get install pastebinit
```

---

