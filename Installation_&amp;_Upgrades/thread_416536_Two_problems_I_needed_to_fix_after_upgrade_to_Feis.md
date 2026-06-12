---
title: "Two problems I needed to fix after upgrade to Feisty"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by t_anjan on 2007-04-21
I upgraded to Feisty on my Compaq laptop. My Edgy was fully updated. The IPW2100 wireless module was configured to connect to my WPA2 router using wpa-supplicant on Edgy. And, my laptop has no SATA drives.

The first problem was that Feisty did not boot after upgrade. 
Booting normally just took me to a "initramfs" prompt.

I got the following message when I booted through the Recovery mode. 

```
ALERT! /dev/hda6 not found.......
```

A little further up in the boot messages, there were references to my hard disk as "sda" instead of "hda" which was what it was on Edgy.

So I edited to boot line in GRUB from root=/dev/hda6 to /dev/sda6 and I was able to boot into Feisty. Then I made the change permanent by editing menu.lst .

The second problem was that my wireless network was not getting detected by the Network Manager applet. After a lot of searching and fiddling around, I found that this guide works: [http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html](http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html)

I had to comment out all the wpa-supplicant lines I had in my "interfaces" file.

---

