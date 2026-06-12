---
title: "Can't install/boot Hardy"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by joemseat on 2008-05-28
Hi All,

I am running an AMD X2 4400+, 2gb ram, Asus A8N SLI Premium Motherboard, Nvidia 8600GT.

I never had problems installing Gutsy or a previous version.

When I try to install Hardy, I get a ton of:
"SQUASHFS error: unable to read page, black xxxxx, size xxx".

I did some research and used the "all_generic_ide floppy=off irqpoll" kernel options and I managed to successfully complete the installation.

However, after installation completes, I reboot and my computer gets stuck **before** grub even launches...

I was expecting that I would have to pass those same kernel options when booting, but since I can't even make it to Grub, I'm not sure what's going on.


Please let me know if I can provide you with more information.

Thanks for the help

---

### Post by Bubba64 on 2008-05-28
Are you dual booting, and it sounds like you used a ISO download to install is this right. I probably don't have an answer for you but to me this info seems pertinent.

---

### Post by nzadLithium on 2008-05-28
when you say grub doesnt start. What message do you get?

---

### Post by joemseat on 2008-05-28
By the way, I have 1 Pioneer IDE DVDRW, which I used to install the OS. I have 2 SATA hard drives - 1 has a good Gutsy install - this is the one I have plugged in right now. The other, I plugged in only during install (after unplugging the HD with Gutsy). The Hardy HD is the only HD I have plugged in when trying to boot Hardy.

> Are you dual booting, and it sounds like you used a ISO download to install is this right. I probably don't have an answer for you but to me this info seems pertinent.

I am not dual booting. Yes, I downloaded and burned the 8.04 32bit desktop ISO.

> when you say grub doesnt start. What message do you get?

It literally doesn't start and there is no message. The following screenshot is what happens: [http://img225.imageshack.us/my.php?image=img1187kv9.jpg](http://img225.imageshack.us/my.php?image=img1187kv9.jpg)

When I have the Gutsy HD plugged in, I get the exact same display, except it doesn't hang there. A couple seconds later I will get the "Starting GRUB" message.

---

### Post by Bubba64 on 2008-05-28
> **joemseat said:**
> By the way, I have 1 Pioneer IDE DVDRW, which I used to install the OS. I have 2 SATA hard drives - 1 has a good Gutsy install - this is the one I have plugged in right now. The other, I plugged in only during install (after unplugging the HD with Gutsy). The Hardy HD is the only HD I have plugged in when trying to boot Hardy.



I am not dual booting. Yes, I downloaded and burned the 8.04 32bit desktop ISO.



It literally doesn't start and there is no message. The following screenshot is what happens: [http://img225.imageshack.us/my.php?image=img1187kv9.jpg](http://img225.imageshack.us/my.php?image=img1187kv9.jpg)

When I have the Gutsy HD plugged in, I get the exact same display, except it doesn't hang there. A couple seconds later I will get the "Starting GRUB" message.

If it was me I would do a fresh install if you have nothing to lose. I have only done fresh installs with the daily alternative due to having only 256 ram on both of my computers, hitting f12 in the 1st second of start up and scanning the CD for any faults then installing. I don't know the probably multiple install methods with the desktop CD but make sure if you use the same one it is not corrupted.

---

### Post by joemseat on 2008-05-28
I guess I didn't make myself clear.

I have 2 SATA hard drives. Only 1 is ever plugged in at once. 1 contains a fresh Gutsy install and I have been booting off that one and using it without any issues since Gutsy came out. As I am writing this post, that is the only hard drive plugged in.

For Hardy, I bought the second hard drive and did a fresh install on it. When I did the install, only this HD was present. Then when trying to boot Hardy, only this HD was present.



I tried the daily alternate CD from today (May 28th) and that didn't help.

---

### Post by nzadLithium on 2008-05-29
try running grub-install
you will need sudo or su

reset up grub on harddisk. It seems like your pc has found your harddisk bootable but when it loads the bootable part it maybe cant find grub or maybe there are errors.

---

