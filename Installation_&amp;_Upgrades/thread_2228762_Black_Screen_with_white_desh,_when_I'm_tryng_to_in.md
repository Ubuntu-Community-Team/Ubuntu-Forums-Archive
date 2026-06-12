---
title: "Black Screen with white desh, when I'm tryng to install ubuntu"
date: 2014-06-09
forum: Installation &amp; Upgrades
---

### Post by Irakli on 2014-06-09
Hello,

I'm trying to install ubuntu, for the first time.
I'd downloaded Ubuntu 14.04 LTS and wrote on the flash drive. with Universal USB Installer...

When I'm booting from flash drive, there is only black screen and white dash.

Can someone help me?

---

### Post by Bucky Ball on 2014-06-09
Did you completely wipe the USB drive and reformat it as FAT32 before you began? Generally required. If there are any files on the USB they will remain and can seriously mess things up (at least this is the case with UNetbootin; it doesn't delete any existing files on the USB dongle).

---

### Post by Irakli on 2014-06-09
Yes I formated flash drive and it's FAT32.
I made everything like this: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by Bashing-om on 2014-06-09
Irakli; Hi ! Welcome to the forum .

Lot's of maybes here, without further info, iffy to pinpoint to any particular.
But, we can try.
Is this a bios or UEFI based operating system ?
Do you have the horse power in that machine to run the high end edition ubuntu ? 

Assuming Bios and 
you have the hosses
and you have a good burn of the .iso as an image:
 
Cold boot the liveUSB, as soon as the bios screen clears depress and hold the right "shift" key, do you now get the language selection screen ? if so ->
escape key to accept the default -> boot options screen.

Let's say at this point there is a graphics driver issue at play here, - that you are running either Nvidia or ATI for the graphics cards - and for a temporary work around;
At this boot options screen press the F6 key -> preset options pop up.
In the options pop up; arrow down in the preset option(s) to "nomodeset" ; space or enter to accept and then the escape key to exit; 
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.

Do you now boot to that GUI desk top in the live environment ?

If you can get this far, we can make the rest happen.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

