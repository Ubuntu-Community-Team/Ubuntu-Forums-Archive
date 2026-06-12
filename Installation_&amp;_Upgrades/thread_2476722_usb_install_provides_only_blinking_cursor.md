---
title: "usb install provides only blinking cursor"
date: 2022-07-04
forum: Installation &amp; Upgrades
---

### Post by Sherman_Willden on 2022-07-04
I have always had a usb install work in the past and I just replaced 20.04 with 22.04 by using the startup disk creator like I have done in the past. The boot recognized the usb and I first get a GRUB screen which leads to the menu to try or install 22.04. After the try and install goes to a blinking cursor I try safe mode which again leads to a blinking cursor. Of course with the other installs I would get the GUI screen. Now I get a text based menu. I am using a compaq 6710b laptop. Old for sure but works like a champ.

Thank you; sherman

---

### Post by yancek on 2022-07-05
Did you verify your download by reading through the link shown on the download page at the official Ubuntu site?  Is this the site from which you downloaded Ubuntu?

[https://ubuntu.com/download/desktop/thank-you?version=22.04&architecture=amd64](https://ubuntu.com/download/desktop/thank-you?version=22.04&architecture=amd64)

---

### Post by sudodus on 2022-07-05
If I understand correctly this computer has a core 2 duo processor. HP/Compaq computer of that age can be difficult to boot. It usually boots best (at least from USB, maybe also from the internal drive), if there is

- BIOS alias CSM alias legacy boot (as opposed to UEFI boot, which was kind of experimental in computers of that age)
- MSDOS partition table
- boot flag on the boot partition (the partition with /boot/grub, which might be the same partition as the root partition)

The iso file of Ubuntu 22.04 LTS, when cloned, works for me to boot an HP Elitebook 8560p with a generation 2 i5 CPU, so I had expected that your computer would have worked too, because the Startup Disk Creator in current versions of Ubuntu is a cloning tool.

- So I agree with the advice by yancek to check with [FONT=Courier New]**sha256sum**[/FONT] that the iso file was downloaded correctly. You could also try with another USB pendrive and/or clone again (maybe there was some file copying error in the cloning process).

If still no luck, the next step would be to try with [mkusb](https://help.ubuntu.com/community/mkusb). *Do not clone*, it would create the same kind of drive as by the Startup Disk Creator.

- Create a live drive using **[FONT=Courier New]dus-iso2usb[/FONT]** (it is a menu option in mkusb-dus)
- Select [FONT=Courier New]**MSDOS partition table, old grub, boot flag**[/FONT] (also menu options)

---

