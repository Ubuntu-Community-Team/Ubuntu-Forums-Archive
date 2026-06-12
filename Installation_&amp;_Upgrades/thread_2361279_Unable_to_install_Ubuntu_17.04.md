---
title: "Unable to install Ubuntu 17.04"
date: 2017-05-14
forum: Installation &amp; Upgrades
---

### Post by eppaen on 2017-05-14
Hi, please let me know if this has been covered before but I was unable to find an answer in this forum.

I got a laptop with the following specs 
***[COLOR=#6a6a6a]Xishan W670R[/COLOR]*** 17.3" Full-HD Matt, Intel Core i7-6700HQ, 16GB DDR4, 500GB SSD + 1TB HDD, GeForce GTX 950M

it previously had W10 and I want to replace that with Ubuntu. I used Unetbootbin to create an USB stick installation and rebooted the PC.
Installation went smooth, I Installed it on a UEFI BIOS and chose to let Ubuntu delete all partitions.
I added the encryption option besides that a normal installation.
The system asked me to reboot after installation, I entered the password and the system froze. (Did the same 3 times)

After that I removed the UEFI option in BIOS and tried re-installing but the PC is freezing on the same spot.
It also freezes when choosing the "Live CD" option

The five dots goes one round, then freezes with 2 white spots and 3 reds. It does the same every time.

Would appreciate any assistanse in this matter

Uploaded an image of the text error here:
[https://ibb.co/djCAo5](https://ibb.co/djCAo5)


Espen

---

### Post by oldfred on 2017-05-15
Probably better to use UEFI boot mode.
But should work either way.

But new systems need newest Ubuntu and may need even newer kernel & support software not yet in current distribution. It takes a while for open source software to catch up with new hardware. 

Some with nVidia find better to use Intel video to install initially. You should have a setting in UEFI to turn on/off video modes.
With nVidia you usually need nomodeset to boot installer and first boot of system or until you install the nVidia proprietary driver.
You also may need other boot parameters in addition.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

I do not know LVM nor encryption as both are advanced modes, so cannot offer much help with those issues.

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

---

### Post by eppaen on 2017-05-15
Thanks for the input.
I tried installing with different prefixes.

In the end I used UEFI BIOS and added the NOMODESET prefix during install.
And did not use LVM as it froze on boot every time I added that.

Everything works fine now

Thanks

---

