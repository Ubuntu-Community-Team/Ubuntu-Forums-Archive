---
title: "Freezes when loading, after upgrade from Ubuntu 17 to 18"
date: 2018-07-13
forum: Installation &amp; Upgrades
---

### Post by sommies on 2018-07-13
Hello,

I am a new Ubuntu user. Version 17 was my first install.:)  When I upgraded to version 18, the computer now locks up when loading.
The computer is a Dell Optiplex 755, with Intel Core 2 Duo.  Let me know if you'd like any other specs from the machine.
I do have a new SSHD in the machine (it replaced the old hard drive, so there is only the one hard drive in it)

So far, I have tried re-installing Ubuntu from a USB boot stick.  (several flavors, and also version 17)
each time, the computer freezes once I select either the "preview" option, or the install option.

Thank you for taking a look!

-Sommies

---

### Post by haja024 on 2018-07-15
Hi, I had a similar problem with a HP laptop, i5 processor and a NVIDIA graphics card. My computer froze every time Ubuntu 18.04 turned on, right after I entered my password, which is kinda frustrating. I still have no idea what does this (this is my first non-Windows OS), however, this has turned out to work for me: in grub, where you can choose between Ubuntu, Advanced options for Ubuntu, and some other stuff (I dual boot with Windows, so I see there the option to boot that, too) go to the Ubuntu option, and press e to edit boot options. there should be a line starting with linux, and ending with 

quiet splash $vt_handoff. 

change that to 

quiet splash acpi_osi=Linux acpi_backlight=vendor $vt_handoff.

from there, press f10. Ubuntu will just this once boot with this setting. A more permanent solution is to edit this line in /etc/default/grub. Just a side note, this correction has been included in one of the newer updates.

---

### Post by sommies on 2018-07-28
Thanks haja024!
how do I get to grub?

---

