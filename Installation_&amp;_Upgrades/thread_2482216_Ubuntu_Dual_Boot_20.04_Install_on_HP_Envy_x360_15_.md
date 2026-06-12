---
title: "Ubuntu Dual Boot 20.04 Install on HP Envy x360 15 Laptop Infinite Loading"
date: 2022-12-24
forum: Installation &amp; Upgrades
---

### Post by cryoworm2 on 2022-12-24
Tried a dual boot on a brand new HP Envy x360 15 laptop w/ AMD architecture and Windows 11 Home. 
Disabled secure boot and shrunk single SSD drive to half.
Installed 20.04 via Rufus and USB stick and install went fine. Made both swap and root partitions.
Moved boot priority in HP BIOS to Ubuntu.
Grub comes up but when Ubuntu is selected presents an infinite loading screen and never boots into the OS.
Tried recovery option from Ubuntu USB and it freezes with lots of lines of text about loading.
Windows 11 seems to be acting slower now as well.
One time it loaded the Ubuntu login screen but froze when password was entered.

Not sure how to proceed.

Cheers!

cryoworm

---

### Post by Frogs Hair on 2022-12-24
You could start with running the boot repair program from the live usb. There is an option to upload a report to paste bin and you can post the link here in needed.Read and select the options carefully.

---

### Post by VMC on 2022-12-24
One thing is to remove quiet from "linux" string. Then F10 to boot. You might see where the hangup is or what is working on.

---

### Post by UltimateCat on 2022-12-28
> **cryoworm2 said:**
> Tried a dual boot on a brand new HP Envy x360 15 laptop w/ AMD architecture and Windows 11 Home. 
Disabled secure boot and shrunk single SSD drive to half.
Installed 20.04 via Rufus and USB stick and install went fine. Made both swap and root partitions.
Moved boot priority in HP BIOS to Ubuntu.
Grub comes up but when Ubuntu is selected presents an infinite loading screen and never boots into the OS.
Tried recovery option from Ubuntu USB and it freezes with lots of lines of text about loading.
Windows 11 seems to be acting slower now as well.
One time it loaded the Ubuntu login screen but froze when password was entered.

Not sure how to proceed.

Cheers!

cryoworm

When you created your partitions for your Ubuntu install did you make the /ext 4 partition bootable with a flag?
Did you create a /boot partition as well?

***When creating partitions manually it's important to allocate enough (MB or GB) for the /boot, /root, /swap and /home partitions.***

You could try using "Gparted Live" and give your /ext 4 partition the boot flag, save the changes, exit the program and reboot. 

I wonder if your HP is so new that the GPU isn't supported in the kernel?

IS this your machine?
[https://support.hp.com/us-en/document/c06033248](https://support.hp.com/us-en/document/c06033248)

---

