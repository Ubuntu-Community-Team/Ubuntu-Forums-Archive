---
title: "Installation Graphics Issue after Grub"
date: 2018-03-12
forum: Installation &amp; Upgrades
---

### Post by robo731 on 2018-03-12
I am trying to install 16.04.4, but after selecting install from the first menu, I see a screen that looks like the attached image. I verified the ISO and made the image with Rufus 2.18. I tried a Manjaro live environment which worked fine. Not sure what the issue could be.
[ATTACH=CONFIG]278918[/ATTACH]

---

### Post by wildmanne39 on 2018-03-12
*Thread moved to **Installation & Upgrades, a more appropriate forum**.*

---

### Post by oldfred on 2018-03-12
What brand/model system?
And particularly what video card/chip.
Often a video issue. You may need nomodeset until you install a proprietary driver.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by robo731 on 2018-03-12
It's a Dell Inspiron 5521. I believe and it is just using Intel integrated graphics. I didn't see "quiet splash" I had "quiet ---" and replaced it with "nomodeset ---" but no luck. However setting ```
acpi_osi=\"Linux\"
``` did the trick. Thanks for the help.

---

