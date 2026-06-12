---
title: "Ubuntu 22.10 not installing"
date: 2023-01-05
forum: Installation &amp; Upgrades
---

### Post by thefanman64 on 2023-01-05
Ubuntu 22.10 will not install, i am on an older legacy bios only computer and am trying to install Ubuntu 22.10 with a flash drive, yes its in MBR and when i boot off of it, it gets to GRUB loading. Then to Welcome to GRUB! But stops there.

---

### Post by grahammechanical on 2023-01-05
> yes its in MBR and when i boot off of it, it gets to GRUB loading. Then to Welcome to GRUB! But stops

Is this happening when you are loading the Ubuntu installer from the flash drive? Or is it happening after the installation process has finished and on the first reboot?

Please tell us the hardware specification of this machine. What CPU? How much RAM? What video adapter? Is this a dual boot with another operating system?

This message, "Welcome to Grub," is that Grub rescue? If you have installed Ubuntu and are being dumped at a Grub Rescue prompt it is because Grab cannot find its configuration files.

Regrades

---

### Post by thefanman64 on 2023-01-05
Its happening after loading the installer, and its a Intel Core 2 Duo E4600 2.4GHz with 4GBs of ram, ive tried it with the onboard graphics adapter and an AMD r5 240 gpu. I am trying to dual boot it with windows 7 but does this no matter if i have the HDD with windows plugged in or not.

---

### Post by thefanman64 on 2023-01-05
Also at the grub prompt there is a blinking cursor but i cannot type. For clarification linux has not yet been installed i am loading off the flash drive, i may try to burn Linux to a dvd soon.

---

### Post by grahammechanical on 2023-01-05
When the installer first loads we get a Grub menu. It will have a Safe Graphics option. You could try using that. I used to have a Core 2 Duo. I found that CPU with 4 GB RAM sufficient for Ubuntu. I now have a more modern Intel Core i7. Loading from USB stick does take a long time. I have just installed 22.04 on another partition. There were moments I thought that the loading of the installer had frozen. For a long time all I saw was a flashing cursor. But eventually the Try Ubuntu and Install Ubuntu screen appeared. I think that during this period Ubuntu is loading into RAM. The installer runs from RAM.

As I remember it, installing from DVD was even slower but you knew something was happening because the spinning of the DVD disc could be heard. The accessing a USB stick is silent. No indication that the USB stick is being accessed.

Regards

---

### Post by thefanman64 on 2023-01-05
I have one main difference, the installer wont load,so i cant access safe graphics. I also tried much older linux variations, even going down to version 4.1,but to no avail. But the flash drive installed to my home server juat fine.

---

