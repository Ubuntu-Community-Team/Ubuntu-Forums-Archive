---
title: "Cant Boot Windows"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by gamingfusion on 2010-01-06
I installed the latest version of ubuntu onto my 4gb flash drive just so i could play around with it, i knwo that it was also a live cd but i thought i would just install it. but now when i boot from my hard drive it uses the GRUB boot loader and wont boot windows at all.
 
how do i fix this?

---

### Post by footloose143 on 2010-01-06
I ran into this situation before, even though you select your usb drive for you installation, somehow it updates your MBR of hard disk if you have not unplugged your HDD while ubuntu installation, the best way is to plug in your USB and login to windows and try running MBRFix(google this tool) or try your windows rescue disk if you have to fix your MBR

---

### Post by kansasnoob on 2010-01-06
> **gamingfusion said:**
> I installed the latest version of ubuntu onto my 4gb flash drive just so i could play around with it, i knwo that it was also a live cd but i thought i would just install it. but now when i boot from my hard drive it uses the GRUB boot loader and wont boot windows at all.
 
how do i fix this?

Boot your Ubuntu Live CD choosing "try without changes ......." and from the Live Desktop post the output of:

```
sudo fdisk -l
```

BTW that's a lower case L.

It would be best to have the external drive plugged in when you boot the Live CD.

---

### Post by darkod on 2010-01-06
> **footloose143 said:**
> I ran into this situation before, even though you select your usb drive for you installation, somehow it updates your MBR of hard disk if you have not unplugged your HDD while ubuntu installation, the best way is to plug in your USB and login to windows and try running MBRFix(google this tool) or try your windows rescue disk if you have to fix your MBR

You don't have to unplug your int hdd. I guess because usb drives are removable devices, the grub bootloader goes straight for the int hdd as fixed location.
During the ubuntu install process, at the last screen, step 4, before clicking the Install button click on Advanced. That will open advanced options where you can select the destination of grub bootloader. Select grub to be installed on your usb drive and that's it.
In this situation you should first reinstall windows bootloader on your int hdd, and then reinstall grub2 on your usb drive MBR. Instructions how to reinstall various bootloaders:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by presence1960 on 2010-01-06
> **darkod said:**
> You don't have to unplug your int hdd. I guess because usb drives are removable devices, the grub bootloader goes straight for the int hdd as fixed location.
During the ubuntu install process, at the last screen, step 4, before clicking the Install button click on Advanced. That will open advanced options where you can select the destination of grub bootloader. Select grub to be installed on your usb drive and that's it.
In this situation you should first reinstall windows bootloader on your int hdd, and then reinstall grub2 on your usb drive MBR. Instructions how to reinstall various bootloaders:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

+1

Right on Darko. no need to open up your case and fiddle around when you can choose exactly where to install GRUB. here is a pick of that window with the Advanced button.

---

