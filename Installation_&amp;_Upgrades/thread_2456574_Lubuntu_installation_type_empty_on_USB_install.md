---
title: "Lubuntu installation type empty on USB install"
date: 2021-01-14
forum: Installation &amp; Upgrades
---

### Post by icewizard8029 on 2021-01-14
I am trying to install Lubuntu version 18.04.5 on my Acer Aspire 3 model N19C1 laptop that already has windows installed onto it. I don't use windows so I want to completely erase it and exclusively use lubuntu. I can't complete the installation because this screen is blank. So far I've tried turning off safe mode in the BIOS menu, but nothing has changed. How can I fix this? 




[ATTACH=CONFIG]287738[/ATTACH]

---

### Post by GhX6GZMB on 2021-01-14
Why 18.04? It's running out of support.
Your machine will work fine with 20.04.1

---

### Post by icewizard8029 on 2021-01-14
I want to use 20.04.1 but when I tried to install that it said my computer does not have enough memory to do the installation. This is a new laptop that I bought with nothing installed onto it besides windows 10, so I'm not sure why there isn't enough memory to install 20.04.1. Even if it's not going to be supported anymore I would rather use it than windows.

Is there some way that I can delete whatever is taking up the memory on my computer so that I can install 20.04.1?

---

### Post by oldfred on 2021-01-14
Have you updated UEFI and SSD firmware? Acer Aspire A315-53-386P remove RAID from drive
[https://askubuntu.com/questions/1167506/the-installation-window-dont-show-a-root-file-system-for-choose-in-the-installa](https://askubuntu.com/questions/1167506/the-installation-window-dont-show-a-root-file-system-for-choose-in-the-installa) & 
Acer Swift 5 (2019) ctrl-s  in UEFI required to be able to change to AHCI mode.
[https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown](https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown)
Older but should be similar. Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by GhX6GZMB on 2021-01-14
> **icewizard8029 said:**
> I want to use 20.04.1 but when I tried to install that it said my computer does not have enough memory to do the installation.

This is a BIOS/UEFI issue. Boot into the setup and remove "fast boot" and also "secure boot" and reboot the machine completely. (the names might be a bit different on your machine, but you get the idea).

Then try again with 20.04. Don't worry, you have plenty of space for Lubuntu. :)

---

### Post by icewizard8029 on 2021-01-14
Thanks ml9104 that worked. I have enough memory now so I'm going to try to install 20.04 instead of 18.04.5

---

