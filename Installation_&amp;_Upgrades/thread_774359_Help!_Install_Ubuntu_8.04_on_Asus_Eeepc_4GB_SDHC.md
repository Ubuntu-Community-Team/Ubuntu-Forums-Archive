---
title: "Help! Install Ubuntu 8.04 on Asus Eeepc 4GB SDHC"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by carlcx on 2008-04-29
I have Asus Eeepc 701 4GB, but I want to install Ubuntu 8.04 on a 4GB SDHC so I can boot on Ubuntu. My 4GB SSD on the Eeepc has crashed and I cannot install anything on it! So, I intend Ubuntu 8.04 on the SDHC to boot as my existing OS.. the problems:
1. How to install Ubuntu 8.04 on a 4GB SDHC (step-by-step please! I am a newbie in Linux;
2. How do I partition the 4GB SDHC?

---

### Post by lemming465 on 2008-05-05
I can't guarantee that Ubuntu 8.04 has drivers for all of your Eee PC hardware.  In your case, I'd suggest picking the first partition option and just letting Ubuntu do what it wants with the entire disk.

See [Ubuntu Eee directions]("https://help.ubuntu.com/community/EeePC") for more detailed guidance.

---

### Post by weblordpepe on 2008-05-31
There's an 'Ubuntu EEE' script which turns your standard Ubuntu 8.08 into an EEE sex machine. 

However what you want to do is after the install process is complete, mount the SD card and edit /etc/boot/grub/menu.lst i think it is.

Because when you boot off the SD card, the SD card is viewed as 0,0 (hard drive 0, partition 0)

---

