---
title: "Black screen with blinking underscore when trying to boot usb"
date: 2014-01-28
forum: Installation &amp; Upgrades
---

### Post by gordo151091 on 2014-01-28
Hello, Im trying to install Ubuntu 12.04 LTS 64 bits on a Gateway NV53, but whenever I try to boot from the usb it shows me a black screen with a blinking underscore. I have tried using diferent filesystems (FAT, FAT32, NFTS) and also diferent iso to usb programa (livelinuxcreator, unebootin and Universal usb). I have tried using two diferent usbs and no avail. I have usb as a first boot priority in the BIOS, I have also tried to restore the BIOS no default settings. Any ideas on how to fix this?

---

### Post by Bashing-om on 2014-01-28
gordo151091; Hi !

That box should run ubuntu just fine.
Just a maybe, the graphics card is no longer supported by AMD - unless you install the legacy version of 12.04.1 -
Make sure you have not checked the box "install 3rd party software" in the initial install stage to preclude an attempt to download a proprietary driver (??). This software additions can be addressed after the install is completed.

Also, might try:
Boot the liveUSB, soon as the bios screen clears depress and hold the left shift key -> language screen; escape key to accept the default;
Grub boot options screen -> f6 key -> boot options, choose "nomodeset" from the drop down menu.
enter to accept and then the escape key to exit; 
enter key again to continue the boot process.

Do you now boot to the GUI ?

[INDENT][INDENT][INDENT]just try'n to help
[/INDENT][/INDENT][/INDENT]

---

### Post by gordo151091 on 2014-01-30
Hey Bashin-om! Thanks for your time writing the response. Reading your first response I thought I could first try installing Ubuntu from a CD  before going deeper in the rabits hole, and guess what it worked. I still have no idea why the computer doesn't boot up usb. I still tried the second method and it didn't work. Thanks again for trying to help me.

:)

---

### Post by Bashing-om on 2014-01-30
gordo151091; Hey,

Great you are up and running ubuntu !

As I suspect, most likely a graphics issue - the most common cause - why ubuntu does not work right out of the gate.
As you have marked this thread as solved, we can pursue the reasons why in a new thread.

[INDENT][INDENT]it's all doable
[/INDENT][/INDENT]

---

