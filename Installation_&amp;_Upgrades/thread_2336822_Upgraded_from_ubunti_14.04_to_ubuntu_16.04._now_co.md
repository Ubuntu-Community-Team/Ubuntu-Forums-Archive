---
title: "Upgraded from ubunti 14.04 to ubuntu 16.04. now computer is crippled."
date: 2016-09-11
forum: Installation &amp; Upgrades
---

### Post by dhrm-77 on 2016-09-11
When computer boots, I get the 5 dots that scroll for a while, then it goes to a blank (black) screen, and nothing more happens.
I found out that, at this point, I do have access to TTY sessions with ALT-F1 - Alt-F6, I can log on, but I only have text access.
By trying various things like apt-get, lightdm, do-partial_upgrade, gedit or various games, I always get similar errors always pointing to some kind of "symbol not defined in libstdc++.so.6 with link time reference".
So I assume that that file is corrupt. It appears to be a binary file, which I couldn't edit anyway with gedit since gedit is crippled as well.
I don't have an option to reinstall with a CD-ROM since the CD-ROM isn't working on that machine. At best I could download something on a USB drive, and install it... if I can found a way to mount the USB drive....
Can someone help?

---

### Post by oldfred on 2016-09-11
What video card/chip? often nomodeset needed as boot parameter.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by dhrm-77 on 2016-09-12
Thanks for replying.
I haven't found what video card or chip, this computer has.
I tried to add "**acpi_osi=**" in Grub, and that didn't help.
I will try something else tonight.
Any other idea? anyone?

---

### Post by Dennis N on 2016-09-12
> **dhrm-77 said:**
> Thanks for replying.
I haven't found what video card or chip, this computer has.
I tried to add "**acpi_osi=**" in Grub, and that didn't help.
I will try something else tonight.
Any other idea? anyone?

For some graphics card information, try in terminal:

```
inxi -G
```

Note: Program inxi may not be part of your default install. You can install it from the Ubuntu repos.

---

### Post by dhrm-77 on 2016-09-16
Ok, here is an update:
I tried reinstalling ubuntu 16.04 again, this time from a USB stick, and that didn't work.
Then, I added "[COLOR=#000000]NOMODESET=1" to [/COLOR]etc/default/grub and it worked. I can now login and have a working system.
Thanks for all your help.

---

