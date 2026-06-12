---
title: "Only black screen with blinking cursor after first installation"
date: 2015-05-08
forum: Installation &amp; Upgrades
---

### Post by Joos_Kiener on 2015-05-08
I tried installing Lubuntu on my old eeePC T91. It was previously running Joli OS 1.2 (Ubuntu 9 based) which now is retired.

I uses the alternate installer for 15.04. The installation went without any issues. However when I now start the PC it never starts booting. It shows the BIOS screen and then just a black screen with a white blinling cursor (blinking line) and then nothing happens at all. Meaning the system does not boot at all. I tried the installation twice with the same result.

Whats the issue? Is it possibly related with the boot manager? I choose to install it to the MBR? Should I choose a different option?

---

### Post by mörgæs on 2015-05-09
Hi, welcome to the fora.

In a live boot of Joli or another distro please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by lgd on 2015-05-09
Seems that you need the [boot option]("https://help.ubuntu.com/community/BootOptions") nomodeset. Follow the pictured guide please.

---

### Post by Joos_Kiener on 2015-05-10
OK. That solved the issue. i might add that when using unetbootin to create the USB stick for installation I did not have the possibility to set this option. Therefore I suggest do use (at least from windows) the tool rufus to create the bootable USB stick. The PC now boots but the touchscreen does not work properly.

---

