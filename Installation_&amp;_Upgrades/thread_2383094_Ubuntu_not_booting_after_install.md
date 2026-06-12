---
title: "Ubuntu not booting after install"
date: 2018-01-20
forum: Installation &amp; Upgrades
---

### Post by stefan987 on 2018-01-20
[COLOR=#111111][FONT=inherit]I just tried to install Ubuntu 16.04.03 LTS on an Acer Aspire ES 11. However upon removing the flash disk and restarting, I got "Device not found". It seems that the common fix suggested to others is to go into the BIOS and change "Select an UEFI file as trusted for executing" so that it boots from shimx64.efi. Unfortunately on my particular machine, this option isn't listed among the settings! I've tried installing grub to the efi partition but the problem remained. Boot-repair didn't work either but produced a few errors. The output can be found here: [https://paste.ubuntu.com/26419111/](https://paste.ubuntu.com/26419111/)[/FONT][/COLOR]
[COLOR=#111111][FONT=inherit]What should I try next? Any help appreciated.[/FONT][/COLOR]

---

### Post by markhoeft on 2018-01-20
I had the same problem. These detailed instructions helped.
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
I also had to make sure that secure boot was enabled (after setting a password).

-mark

---

