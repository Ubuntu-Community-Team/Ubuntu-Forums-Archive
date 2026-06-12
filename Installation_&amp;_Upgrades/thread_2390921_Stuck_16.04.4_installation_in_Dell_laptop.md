---
title: "Stuck 16.04.4 installation in Dell laptop"
date: 2018-05-03
forum: Installation &amp; Upgrades
---

### Post by jimhce on 2018-05-03
Hi,

I tried to install 16.04.4 to Dell laptop Inspiron 15 7000, the installation started then stuck without any error message, the [http://www.dell.com/support/article/au/en/audhs1/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](http://www.dell.com/support/article/au/en/audhs1/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en) seems able to install 16.04, appreciate any helps.

Thank you.

Kind regards

---

### Post by linux4me on 2018-05-04
I had 16.04.3 run out-of-the-box on my Inspiron 15 7567, but 16.04.4 hung on me, so I bypassed it and used 17.10 (now I'm using 18.04).

If you want to run 16.04.4 or a later version, make sure you:
[LIST=1]
[*]Update to the latest version of the BIOS.
[*]Set the SATA mode to "AHCI" in the BIOS (by default, it comes set to "RAID," even if you only have one drive).
[*]Turn off Secure Boot in the BIOS.
[*]Set fast boot to "thorough," which is the apparent option to disable fast boot in the BIOS.
[*]If it still locks up, add the "nomodeset" option to the linux line in grub edit mode when launching the live USB. To enter grub edit mode, type "e" when you get the UEFI install screen with the options to try, install, etc. Add "nomodeset" right after "splash" on the next-to-last line (I think), then hit F10 to boot.
[/LIST]

You should be able to complete the installation after doing that, though you may run into some video-driver-related issues with hangs or black screens after rebooting that are fairly easily resolved.

---

### Post by tinylagarto on 2018-05-04
16.04 is still supported but the newest long term release 18.04 just came out. Why not try it?

---

### Post by linux4me on 2018-05-04
> **ivanovnegro2 said:**
> 16.04 is still supported but the newest long term release 18.04 just came out. Why not try it?

+1

---

