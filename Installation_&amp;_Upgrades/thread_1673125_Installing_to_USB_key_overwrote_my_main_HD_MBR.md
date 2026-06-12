---
title: "Installing to USB key overwrote my main HD MBR"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by mvidberg on 2011-01-21
I wanted to install Ubuntu 10.10 onto a 16Gig USB key and did so by booting with a Live CD and doing the install to /dev/sdc1 (which is the USB key).

It installed fine to the USB but it also installed grub MBR to /dev/sda1 (doh!) .. so now I can't boot into my main HD unless I have the USB key plugged in and I select the correct kernal on /dev/sdc1 to load from on the grub boot menu.   If I try booting without the USB key I get...

error: no such device: <long device id number here>
grub rescue> _

Um... so how do restore my MBR on /dev/sda1?

---

### Post by JOHNNYG713 on 2011-01-21
If you can boot to your Main drive install with the flash drive installed, (via grub menu) do so and once there try opening terminal and run the command **sudo update-grub**, then try a reboot without the flash drive installed, see if that works!

---

### Post by Quackers on 2011-01-21
If your main hard drive only has Windows on it you will need to repair the mbr with a Windows repair disc. That will restore the Windows bootloader to the mbr. To install grub to the mbr of your flash drive you can boot from it and once in Ubuntu you can run these terminal commands
```
sudo grub-install --recheck /dev/sdc
sudo update-grub
```
Note that sdc is named, not sdc1
This assumes that your flash drive is still named sdc by the system.

---

### Post by mvidberg on 2011-01-22
Thanks for the help!  

Unfortunately, doing just 
sudo update-grub
after booting into sda1 didn't fix it... as I guess it was just modifying the stage 2 boot sector, not the stage 1.

So here is what I did to get both working.

Booted into sdc (USB key) and did the following

sudo grub-install --recheck /dev/sdc
sudo update-grub

Then I booted into sda (my main HD) and did the following

sudo grub-install --recheck /dev/sda
sudo update-grub

---

