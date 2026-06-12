---
title: "need help withe wireless drivers in a new kubuntu installation"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by steve19137 on 2010-01-20
so i managed to install kubuntu on my 80GB usb drive, and it works great except for the wireless. i read quite a while ago (in the ubuntu wiki or some related site) that the wireless driver for my computer were put into ubuntu 8.10, but not any versions after that. this is my computer

Compaq Presario C551NR
Internal Drive: Ubuntu 9.10 (started with Ubuntu 8.10, then upgraded)
External Drives: 80GB Drive with Kubuntu 9.10, 80GB Drive with openSUSE.

i dont know what my wireless card is exactly, but if there is a way to download my wireless drivers and install them, please help.

---

### Post by djchandler on 2010-01-20
> **steve19137 said:**
> Compaq Presario C551NR
Internal Drive: Ubuntu 9.10 (started with Ubuntu 8.10, then upgraded)
External Drives: 80GB Drive with Kubuntu 9.10, 80GB Drive with openSUSE.

We need to know what WLAN chipset is used in your laptop. Can you go to Computer>Properties>Devices and find out in Vista?

But my research shows it's possibly a Broadcom 4311 chipset, no thanks to HP support BTW. Broadcom apparently doesn't release code to FOSS development. You can get an executable binary from Broadcom. It appears to be a monolithic installer, neither dependent on Linux kernel version, Linux distribution flavor or the specific Broadcom WLAN chipset.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Let us know how this turns out either way. Please mark the thread "solved" when your particular issue is solved.

---

### Post by steve19137 on 2010-01-21
> **djchandler said:**
> We need to know what WLAN chipset is used in your laptop. Can you go to Computer>Properties>Devices and find out in Vista?

But my research shows it's possibly a Broadcom 4311 chipset, no thanks to HP support BTW. Broadcom apparently doesn't release code to FOSS development. You can get an executable binary from Broadcom. It appears to be a monolithic installer, neither dependent on Linux kernel version, Linux distribution flavor or the specific Broadcom WLAN chipset.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Let us know how this turns out either way. Please mark the thread "solved" when your particular issue is solved.

i dont dual boot vista for the very reason of viruses. they seem to hunt me down. or vise versa ;), but heres what i was thinking at school.

i have a copy of ubuntu 8.10 burned to a cd-r, never to be erased. i could install that to my external hard drive, install kde, and remove gnome using [this post]("http://ubuntuforums.org/showpost.php?p=226502&postcount=2"). i would enable the hardware drivers, then install kubuntu 9.10 from my cd-rw. would that work? or would i have to obtain a copy of kubuntu 8.10?

---

### Post by steve19137 on 2010-01-21
i figured out what wireless card i have with a program that i downloaded from the sources. im not sure what it means, cuz im not a hardware guy, so i posted a screenshot.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=144418&stc=1&d=1264109930[/IMG]

i did this from my internal ubuntu installation. if i like kde enough, and can get the wireless working, i will make kde my internal installation.

---

### Post by steve19137 on 2010-01-23
bump.

---

