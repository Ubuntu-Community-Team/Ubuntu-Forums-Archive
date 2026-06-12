---
title: "ubuntu installation"
date: 2013-03-13
forum: Installation &amp; Upgrades
---

### Post by Iqbal_ on 2013-03-13
Hi,

Recently the motherboard of HCL 64bits laptop damaged and repaired thereafter. It was discovered that some nvidia chip has damaged. So the nvidia chip was replaced.
Now after repaire, the wi-fi is not recognised in ifconfig command.
For installing ubuntu, I have choose nomodeset boot option. But the F6 is not working after repaire.

Is there any way to choose nomodeset boot option without using F6?
 I use usb to install.

Any help on wifi?

thank you...

---

### Post by ibjsb4 on 2013-03-13
Tapping the "shift key" during boot should get you to your grub screen.  From there ..

 [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by grahammechanical on 2013-03-13
At the Grub menu select Ubuntu and press E. That will put grub into Edit mode. It will also stop the countdown timer. Find the line that begins 

> linux /boot/vmlinuz- and ends > ro quiet splash insert nomodeset between ro and quiet > ro nomodeset quiet splash F10 should let you boot.

Another way to do this is to select Recovery mode and at the next screen select Resume. That will load Ubuntu without activating a video driver.

As regards WiFi, it could be that the repair people switched off the wireless adapter at the keyboard or disabled it in the BIOS. If wireless is switched off in Windows it will not be switched on in Ubuntu.

Regards.

---

### Post by Iqbal_ on 2013-03-14
Hi,
What I have been doing is I mount ubuntu bootable usb in another laptop and edit the file in boot folder. This file contains the enteries 1- Try ubuntu without installing and 2- Install ubuntu.

I add nomodeset after quite splash -- and save the file.
When I boot the laptop with this usb then same problem - laptop does not boot.

---

### Post by Iqbal_ on 2013-03-14
Hi,
I read in one of the ubuntu forums that open the usb and add nomodeset boot option in the kernel line in the txt.??? in syslinux folder. Now booting from usb worked.
So I could set nomodeset boot option without using F6 key.

After repaire some of the keys are not working.
I installed 12.04.

Wifi is still a problem. I could not find anything in BIOS (Post #3) regarding wifi.

---

