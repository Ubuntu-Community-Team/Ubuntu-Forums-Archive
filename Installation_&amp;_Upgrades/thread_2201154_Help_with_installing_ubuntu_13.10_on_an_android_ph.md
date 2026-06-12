---
title: "Help with installing ubuntu 13.10 on an android phone"
date: 2014-01-22
forum: Installation &amp; Upgrades
---

### Post by adrian_b2 on 2014-01-22
i want to "install" ubuntu 13.10 on my phone, so i've downloaded the os(3.72gb),and i have installed androidVNC and i Have CompleteLinuxInstaller  and my phone is rooted,it's an Samsung Galaxy S4, without knox,that has CyanogenMod on it(Version 11.0) and the android version is 4.4.2 ,the kernel is 3.4.0-cyanogenmod-g5a32c11build04@cyanogenmod #1 Thu Jan 9 21:12:16 PST 2014 was the time the kernel was launched, i checked if my phone is loop compatible using, the following in terminal emulator : [FONT=Droid Sans Mono]zcat /proc/config.gz | grep CONFIG_BLK_DEV_LOOP , i found it on this webpage (the last comment)  [/FONT]http://android.stackexchange.com/questions/25396/how-to-find-out-if-my-devices-kernel-has-loop-device-support , and i got y, that means it is a loop device, but when i ran CompleteLinuxInstaller i got into the following problem

Checking loop device ... FOUND
mount: mounting /dev/block/loop255 on /data/local/mnt failed : Invalid Argument 
ERROR: Unable to mount the loop device

so if you can help, me i am not a genius, just tell me the simplest way to fix this.

Thanks in advance

Adrian B,

---

