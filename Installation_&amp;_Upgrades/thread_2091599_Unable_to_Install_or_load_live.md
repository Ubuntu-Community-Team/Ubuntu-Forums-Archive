---
title: "Unable to Install or load live"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by sschevy010 on 2012-12-05
I have been trying to install Ubuntu 12.10 x64, I have also tried previous version as well as 32bit. I keep getting this message in the picture.. Is there a work around or what issue is this that I am having?

---

### Post by trogdor1138 on 2012-12-06
Nouveau is the open source Nvidia GPU driver, so you probably have a Nvidia graphics card, right? Could you specify which one specifically, particularly the GPU and the number/types of outputs?

---

### Post by sschevy010 on 2012-12-07
> **trogdor1138 said:**
> Nouveau is the open source Nvidia GPU driver, so you probably have a Nvidia graphics card, right? Could you specify which one specifically, particularly the GPU and the number/types of outputs?

Yeah, I have Nvidia Geforce ENGT240 1gb GDDR5 by ASUS.
I just installed Fedora 17 since it has a basic driver mode unlike ubuntu and installed the correct drivers for it which performs great, but still rather use Ubuntu if any way i can run it...
Unless there is a basic mode on Ubuntu to install it...

Also to add, Using ASUS M4A87TD EVO/USB3 with Phenom II X6 1055T
8GB of 2000mhz Memory with 3 HDD when 2 are on RAID 0

---

### Post by sschevy010 on 2012-12-07
Is there a thread or somewhere where i can get guidance on installing this??

---

### Post by sschevy010 on 2012-12-08
So i found a work around, but still ending up with another issue.. but I think i screwed up something in between the task.

What I did to work around:

Downloaded the Windows Installer
-Installed it to my spare drive
-reboots, gives me option to select how i want to boot.. Tried each selection of what i thought may work which was basic drivers and low graphic... those did not work, I have chosen ACPI Workaround and that worked beautifully..
-Managed to install Ubuntu, but after reboot, still getting same problem but this time, Was able to use recovery mode.. when in there i chose normal boot (which as you know boots as low graphic)
-able to get it to run now, but the difficult task was.. so i ran updates for which made it current, still have to use recovery mode..
-finding out what kernel am i Missing and i think i installed wrong items and also installed Nvidia binaries (current) for which however the nvidia drivers from Nvidia would not install, well, it did but kept saying linux-headers-3.5.0-19-generic package required for which it is installed on the system i thought? it shows it in Grub..
-but after rebooting it.. i was able to run normal but after log in... all i get is a wallpaper, not sure what I need to look for, but what is next step here?

Edit:

What I dont understand is, why is the windows installer have that option to boot that way and not the USB/CD/DVD ??

---

