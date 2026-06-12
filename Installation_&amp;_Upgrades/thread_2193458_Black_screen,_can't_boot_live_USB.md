---
title: "Black screen, can't boot live USB"
date: 2013-12-13
forum: Installation &amp; Upgrades
---

### Post by wishingstar on 2013-12-13
Hello all,

I'm having an issue booting from a USB with kubuntu. I get grub and when I select "start kubuntu" i get nothing, just an empty screen (no splash screen), the USB stick flashes a bit and then nothing, I would have to do a hard reset. Here's what I've tried so far:

Kubuntu 13.04, with and w/o persistence
Kubuntu 13.10, with and w/o persistence
Tried creating live USB stick using UNetBootin and LiLi (for all cases)
All the time USB was formatted as FAT32

My hardware is: AMD A8 Quad Core, Integrated ATI graphics (Radeon HD 7640G), 6GB RAM

Thanks!

---

### Post by nerdtron on 2013-12-13
Have you tried booting the live USB from another computer, just to make sure that the USB has complete files?

---

### Post by BenjaminCHILOE IS. on 2013-12-13
Yes, firstly try your usb kubuntu OS in another laptop or PC, see if it can boot up and if not, I would suggest you download a new kubuntu iso and then burn it or use unetbootin again..and format your usbstick with some disk utilty for fat32 ( Disks is included for fomatting in ubuntu.)

The best

---

### Post by wishingstar on 2013-12-13
I just tried the USB on my friend's laptop, everything works fine. I'm thinking it's a secure boot issue. I tried to follow the instructions here:

[http://forums.linuxmint.com/viewtopic.php?f=46&t=140874](http://forums.linuxmint.com/viewtopic.php?f=46&t=140874)

but it still didn't work. I would appreciate any other ideas :)

---

### Post by bhgrove on 2013-12-13
I am having the same issue with my alienware 18 Because I get to the splash that asks try Ubuntu or boot I don't think it is an issue with the BIOS. I wonder if it has to do with the GUI. I have two NVIDA GeForce GTX 770Ms. running windows 8.1. Any Ideas?:confused:

---

### Post by wishingstar on 2013-12-14
J actually just managed to get this to work, for some reason. The first USB stick I made with UNetBootin worked on other computers (it was a 4GB stick). I then created a new one (also with UNetBootin, formatted as 32bit) but this one was a 2GB stick, then following the instructions on the link I provided from the Mint forums, it finally worked and I was able to install Kubuntu 13.10. So here's what I did:

1- Create 2GB USB stick, formatted as fat32 using UNetBootin
2- Go into BIOS, set the SATA mode to IDE, Turn off Fast Boot, then turn CSM and PXE on
3- Restart and go into BIOS again, set the USB stick to be first in boot order
4- Reboot, this should get you into graphical UNetBootin Grub
5- Just hit start kubuntu, you don't need to change any of the startup parameters (no need for xforcevesa or nosplash)
6- When formatting the hard drive to run linux as the only OS (which is what I did), create a 10-100MB partition at the beginning of the drive and set it to BIOS reserved

All done! I'm marking this as solved, I just posted the details on how it worked in case anyone else faces the same issue :)

---

