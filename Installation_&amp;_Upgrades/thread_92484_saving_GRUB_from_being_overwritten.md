---
title: "saving GRUB from being overwritten"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by Brando569 on 2005-11-19
whenever i have linux installed and then install windows it overwrites the MBR and erases GRUB. all of the methods i have found for restoring GRUB dont work for me at all and i end up having to reinstall my root partiton. ive tried using a live cd to reinstall grub, i think that might of worked once, ive tried going into the installation via expert mode and trying to install it that way, and it always says that there was an error and it cannot continue. ive tried simply, going into rescue mode and at the terminal typing grub and it always says "error opening bterm". ive even tried loading grub off of this cd i have (UBCD) and pointing it to my root partition and it says the kernel cant be found. are there any other sure fire ways that would work? i saw an option in fdisk where you can save the mbr to a file then restore it at a later date. would that work? and running windows inside a vm wouldnt work cuz i need to have access to my serial ports or else i would use VMware for it.

---

### Post by aysiu on 2005-11-20
Why are you reinstalling Linux *and* Windows so often?
There is a way to have a dual-boot with Windows' boot loader in charge of the dual-boot. That may help you. Do a Google search for *dual boot linux windows linux.bin boot.ini*

---

### Post by Brando569 on 2005-11-20
first windows didnt wanna work at my college so i switched to ubuntu and completely got rid of windows. then about a month later my car started screwing up and i have a data logger/code reader that connects to my serial port and i dont think i can access the serial port through a VM (or can i?) so i figured the only way to get it to work was to install windows, and when you install windows it erases grub...

---

### Post by Peter Scales on 2005-11-20
Most versions of WIN will overwrite the MBR ... particularly WIN9x
 The workaround is win install 1st .. then linux
or use the linux install to rewrite the MBR only - not the full install

---

### Post by Brando569 on 2005-11-20
both of those arent really options for me cuz when i already have linux installed, i need windows for something, and once windows overwrites the mbr i cant do ANYTHING with grub.

---

### Post by aysiu on 2005-11-20
[QUOTE=Brando569]both of those arent really options for me cuz when i already have linux installed, i need windows for something, and once windows overwrites the mbr i cant do ANYTHING with grub.[/QUOTE] [Yes, you can](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by Brando569 on 2005-11-20
whenever i try to use that method and try to install grub it gives me an error that it cant.

---

### Post by aysiu on 2005-11-20
[QUOTE=Brando569]whenever i try to use that method and try to install grub it gives me an error that it cant.[/QUOTE] Which method? The install CD or the live CD method?

---

### Post by Brando569 on 2005-11-20
the instal cd, i think the live cd method might have worked for me idk i cant remember..

---

