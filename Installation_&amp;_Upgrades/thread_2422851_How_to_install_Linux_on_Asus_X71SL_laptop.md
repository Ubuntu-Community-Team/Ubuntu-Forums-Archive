---
title: "How to install Linux on Asus X71SL laptop"
date: 2019-07-13
forum: Installation &amp; Upgrades
---

### Post by nodjoim on 2019-07-13
I have tried various ISO's from different distributions and both 32 and 64bit to install Linux on an Asus X71SL laptop but to no avail!
I cannot even run a live-USB.
It sees the USB and even boots from it but after the initial screen all I get is a black screen with blinking cursor.

Any help is greatly appreciated!

---

### Post by DuckHook on 2019-07-14
Your laptop is not that old and should run well:

[LIST=1]
[*]Stick to 64-bit. You should have no problem running that, and 32-bit is quickly becoming obsolete.
[*]Depending on amount of RAM, try using Xubuntu, Lubuntu, Mate or Budgie. If 1 GB RAM or less, use Lubuntu. For options on low-resource DEs, see the link in my sig: "The Best 'buntu Flavour"
[*]Try using nomodeset at LiveUSB boot. [Instructions here]("https://help.ubuntu.com/community/BootOptions"). You may need to install closed-source NVidia driver afterwards. I can't help you there as I haven't installed such a driver in years.
[/LIST]

---

### Post by Topsiho on 2019-07-14
Try Q4OS. It's really great and revives the old KDE3 days, if that means anything to you. If not: just try it. It saved the day for my Acer Aspire One netbook, from 2008, which runs well on this very nice very small footprint OS. Also 32 bits is still maintained.

Topsiho

---

### Post by oldfred on 2019-07-14
It shows a nVidia 9300 video chip.

You probably just need nomodeset boot parameter. At tiny accessiblity icons at bottom of screen press "any" key and then f6 to add nomodeset. Some systems may also need additional parameters.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter](https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter)

---

