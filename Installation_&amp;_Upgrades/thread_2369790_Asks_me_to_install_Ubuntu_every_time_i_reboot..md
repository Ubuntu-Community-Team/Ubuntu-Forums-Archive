---
title: "Asks me to install Ubuntu every time i reboot."
date: 2017-08-26
forum: Installation &amp; Upgrades
---

### Post by jay365 on 2017-08-26
After finishing my ubuntu installation it asks me to restart my computer to finish the installation. I do this and it either takes me back to windows 10, or if I press F12 and select my external hard drive (with Ubuntu on it) it asks me to: try ubuntu without installing, Install Ubuntu etc. I have tried to reinstall it about 5-6 times without luck as the same issue occurs and I have checked over the internet without finding any solutions that worked. I am using Ubuntu 17.04 on a external hard disk drive. I have tried the MBR Partition Scheme for both BIOS and UEFI (with rufus) and the same thing happens. My computer is an Intel Core i7-7500U 2.70Ghz. I have 8GB of RAM and use Intel HD Graphics 620 (I use a laptop). My computer has windows 10 installed on its C Drive and I have Ubuntu on a external drive. The File system I am using is Large FAT32 and the cluster size is 32 Kilobytes. Please Help!

Thanks in advance.
Jay.

---

### Post by wheatpenny2 on 2017-08-26
The problem is your boot order. It's booting from your main hard drive. Go into Windows and press Shift and Restart at the same time and it will take you to a configuration screen (I no longer have Windows 10 so I'm doing this from memory and my memory may be a bit off)  "Select "troubleshoot". There will be options to refresh or reset your computer, and an "advanced options" box. Select that, then on the screen that comes up select "UEFI Firmware settings". When the UEFI settings (aka BIOS) board comes up, first go to "security" and disable "secure boot", then go to "Boot" (or "startup" depending on the brand of your computer) and there is amenu (I don't recall what it says exactly, and Google was of no help), but one of the entries has an arrow next to it. Select that and hit enter and there is the boot order. Move Ubuntu to the top. then save your changes and restart.

---

### Post by jay365 on 2017-08-27
> **wheatpenny2 said:**
> The problem is your boot order. It's booting from your main hard drive. Go into Windows and press Shift and Restart at the same time and it will take you to a configuration screen (I no longer have Windows 10 so I'm doing this from memory and my memory may be a bit off)  "Select "troubleshoot". There will be options to refresh or reset your computer, and an "advanced options" box. Select that, then on the screen that comes up select "UEFI Firmware settings". When the UEFI settings (aka BIOS) board comes up, first go to "security" and disable "secure boot", then go to "Boot" (or "startup" depending on the brand of your computer) and there is amenu (I don't recall what it says exactly, and Google was of no help), but one of the entries has an arrow next to it. Select that and hit enter and there is the boot order. Move Ubuntu to the top. then save your changes and restart.

I can change my secure boot but nothing of what you described was in the "Boot Menu". There was the order of how my components boot and I had already changed windows boot agent to the last and my USB HDD to first. For some reason it still boots to windows so I can't actually stop it from booting to my C drive unless I manually stop it. My UEFI/BIOS doesn't let me disable windows from booting it only lets me change the order so to boot with Ubuntu I would have to press F12, however when I do this, it restarts the whole installation instead of discovering existing files. Again, I have found ZERO solutions on the internet, if anyone has, can they please link me the website.

Thanks
Jay.

---

### Post by Autodave on 2017-08-27
I am assuming that you are removing the installation medium *before* rebooting the PC?

---

### Post by jay365 on 2017-08-27
> **Autodave said:**
> I am assuming that you are removing the installation medium *before* rebooting the PC?

By that do you mean the hard drive I have with Ubuntu on it. If you do, how can I remove it when I have the operating system on it. Please tell me what you mean and if there are any websites telling me how to do this, please link it to me.
Thanks for the help!
Jay

---

### Post by oldos2er on 2017-08-27
Your installation medium is the USB flash drive (or DVD) you used to install Ubuntu, not a hard drive.

---

