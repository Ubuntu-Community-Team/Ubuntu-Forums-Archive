---
title: "ubuntu installation stuck"
date: 2014-12-15
forum: Installation &amp; Upgrades
---

### Post by first-trivin on 2014-12-15
I'm trying to install ubuntu 14.04.1 on an old PC, core 2 duo E8300, from DVD.
It boots from disk fine. But then I get to an empty screen with the ubuntu default wallpaper and the toolbar in the top of the screen. On the right side of the toolbar there are several icons: the gear, language, sound, network and a blue circle with a white man inside. The keyboard and the mouse are not responding and there is nothing I can do to continue the installation.
I tried installing both the 32 bit version and the 64 bit version, same result.

please help :(

---

### Post by oldfred on 2014-12-15
How much RAM, and what video card/chip?

Better to use 64 bit if you have 2GB or more of RAM.

Is this the live installer or after you have installed?

Some BIOS require you to turn on USB support for keyboard & mouse. I have to do that with my older system. Both Windows & Ubuntu did not need that, as they seem to have their own drivers by-passing BIOS. But grub is using BIOS settings so you need that turned on.

---

### Post by Bashing-om on 2014-12-15
first-trivin; Hi ! My Welcome to the forum .

"oldfred" beat me to it .. said what I had in mind.

Reset bios setting for USB devices AND make sure " plug and play" is enabled . Get the liveDVD to boot to "try ubuntu" mode and we take it from there .

[INDENT][INDENT]we work to get ya up on 'buntu
[/INDENT][/INDENT]

---

### Post by first-trivin on 2014-12-15
It has 2 GB ram at list, maybe 4, and the video card is Nvidia Geforce 6800 GS.
It is a live installation, in the beginning of it.
The keyboard and the mouse are connected via PS/2 connectors.

---

### Post by Bashing-om on 2014-12-15
first-trivin;

PS/2 keyboard calls for "legacy" settings in bios. ( I too run an old PS/2 mechanical keyboard )

Dual core and 2+ gigs of ram, should run ubuntu just fine.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by first-trivin on 2014-12-15
It's working. I enabled everything in the bios(the USB keyboard and mouse support was disabled). Then booted to "try ubuntu" and installed from there.
I'm not sure which of the two did it but it's installing now.

Thanks

---

### Post by oldfred on 2014-12-15
With nVidia board, you probably will need nomodeset to boot live installer and first boot or until you install the nVidia driver from the Ubuntu repository. 

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

It looks like you need the 304.xx legacy driver.
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

