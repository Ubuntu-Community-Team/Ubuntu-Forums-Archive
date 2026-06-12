---
title: "hard drive only install help?"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by wyrmeth on 2010-07-15
[B][I][FONT="Palatino Linotype"][SIZE="3"][COLOR="Navy"]Basically im new to ubuntu ive got two laptops that have no cd drives and cant boot from usb. I heard it is possible to remove the hard drives connect them as external hard drives (in a caddy i have already)to a windows machine and setup the installation files. Ive tried installing the live install on usb to the hdds and while it tries to work it always errors saying it cannot unmount the harddrive. I think this is because of the type of installation and i need lilo is it? maybe someone can point me to a step by step instruction on how to configure the installation files? and stop me pulling my hair out

cheers

wyrmeth[/COLOR][/SIZE][/FONT][/I][/B]

---

### Post by oldfred on 2010-07-15
Are you trying to install from the same drive you want to install to? That will not work.
If you can boot USB, use a USB flash drive to install to the USB hard drive. If on another computer you can also install the ISO to a CD and install from the CD. 
The only way to install from the same hard drive may be to have a separate 1GB install partition(primary) on the drive and then install to the rest of the drive. I think I have seen a way to do this but do not have a link.

---

### Post by wyrmeth on 2010-07-15
> **oldfred said:**
> to have a separate 1GB install partition(primary) on the drive and then install to the rest of the drive. I think I have seen a way to do this but do not have a link.

***[FONT="Palatino Linotype"][SIZE="3"][COLOR="Navy"]This is exactly what i want to do ive got a windows laptop that can run the live cd ive tried partitioning the drive but it doesnt seem to work thats why im looking for a step by step guide[/COLOR][/SIZE][/FONT]***

---

### Post by wyrmeth on 2010-07-15
**[FONT="Palatino Linotype"][SIZE="3"][COLOR="Navy"]i think these are the instructions but im not sure how to set it up[/COLOR][/SIZE][/FONT]**

[http://www.plop.at/en/bootmanager.html#grubinst](http://www.plop.at/en/bootmanager.html#grubinst)





```
Harddisk install using LILO

Download the current boot manager plpbt-5.0.10.zip. Extract it to get the boot manager install program. You find the install program plpinstc.com in the install directory.

Copy plpinstc.com to /boot.

Add to your /etc/lilo.conf the following

image=/boot/plpinstc.com
label=plop-install
Run lilo to update lilo.
```

***[FONT="Palatino Linotype"][SIZE="3"][COLOR="Navy"]so ive got a blank my hard drive ready do i create a folder /boot?? do i need to copy anything else?[/COLOR][/SIZE][/FONT]***

---

### Post by oldfred on 2010-07-15
Those instructions mention that it will be in your grub menu after you reboot so that is a Linux install.

If you have your drive plugged into another computer, does that computer boot a CD or USB. If so then install from those.

---

### Post by wyrmeth on 2010-07-16
> **oldfred said:**
> Those instructions mention that it will be in your grub menu after you reboot so that is a Linux install.

If you have your drive plugged into another computer, does that computer boot a CD or USB. If so then install from those.

***[FONT="Palatino Linotype"][COLOR="Navy"][SIZE="3"]I thought each installation was unique to the computers hardware? Didnt think this would work ... ok i guess its worth giving it a whirl thx m8[/SIZE][/COLOR][/FONT]***

---

