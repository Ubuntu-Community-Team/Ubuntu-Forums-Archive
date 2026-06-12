---
title: "Can't boot up Ubuntu 16.04.2 or 17.04 on USB"
date: 2017-04-25
forum: Installation &amp; Upgrades
---

### Post by renanrischiotto1 on 2017-04-25
I'm trying to install Ubuntu GNOME on my computer but I'm not having success. After selecting in BIOS to boot from USB, the screen turns black with many white scratches and stays there forever.

This happens with both Ubuntu 16.04.2 and 17.04. At the moment I'm wanting to install Ubuntu 17.04 GNOME (where the same problem occurs).

Video showing the problem: [https://www.youtube.com/watch?v=r0-fVcGN4Nk](https://www.youtube.com/watch?v=r0-fVcGN4Nk)

--> USB OK, ISO image OK.

Computer specs below:

ASUS B85M-E / BR
I5-4460
GTX 970
12GB RAM
HDD 1TB

Linux Mint 18.1 installs just fine, I think it's because uses a "old" kernel (?)

***sorry my english***

---

### Post by oldfred on 2017-04-25
With nVidia card/chip, you probably need nomodeset to boot installer and inital boot of install or until you install nVidia driver from repository.
How you add nomodeset depends on if installing in BIOS or UEFI boot mode. After install you edit grub.

You may need other settings in UEFI/BIOS and possibly other boot options also.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by renanrischiotto1 on 2017-04-25
Hi! Thank you man! I used the "nomodeset" option and worked perfectly!

I used 2 times, before the installation and after (on the first boot), then I installed the NVIDIA non-free driver).

:D

---

