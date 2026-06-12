---
title: "No keyboard imput"
date: 2014-05-30
forum: Installation &amp; Upgrades
---

### Post by jakob3 on 2014-05-30
I just got a dell poweredge 840 server with no OS.  When I tried to install ubuntu server 14.04 the USB keyboard refuses to work, as soon as the disk starts to load it is almost as if the keyboard just turns off.  I checked and the keyboard is fine in BIOS and on other machines.  I also tried the keyboard on the server while running Ubuntu Desktop 14.04 to confirm there was no problem with the machine and it was fine then.  I was just wondering if anyone else has had this problem and if there was a way to fix this. Thanks.

---

### Post by Bashing-om on 2014-05-30
jakob3; Hi !  Welcome to the forum .

We do on occasion run into this, that the installer has no driver for the keyboard once bios hands off.
What you might do is change the keyboard options in bios to that of legacy and try once more to install, or change the plug and play options.
Else, does the box support PS/2 input, and DO you have an old PS/2 keyboard laying around ?
Try installing with the PS/2 keyboard.

It can be hoped that once installed the kernel will pick up the keyboard with the proper drivers. The kernel is pretty smart about things like this.
But, I have seen those times that the kernel has the drivers, but grub does not.. can also be a pain with no keyboard while booting.

Times like this
[INDENT][INDENT][INDENT]all we can do is try and see what combination works
[/INDENT][/INDENT][/INDENT]

---

### Post by jakob3 on 2014-05-31
Ok so I changed it to legacy and that didn't work but thankfully my friend let me borrow his old PS/2 keyboard and that worked.  Thanks for the help.

---

### Post by Bashing-om on 2014-05-31
jakob3; Hey,

At least something is working out.

Appears that bios and grub are not talking the same language, now that you are installed and all updated/upgraded -> does the usb keyboard now function - both at booting and as well as when the operating system has booted up ?

There is that possibility that all is well now with "plug and play" devices.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jakob3 on 2014-05-31
Yes it does now work with the USB keyboard

---

### Post by Bashing-om on 2014-05-31
jakob3; Outstanding !


Ain't ubuntu wonderful.

[INDENT][INDENT][INDENT]all's well than ends well
[/INDENT][/INDENT][/INDENT]

---

