---
title: "how do I make a usb boot drive from ubuntu TERMINAL"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by trevorbsmith on 2011-01-04
I tried posting before but got no help.

[http://ubuntuforums.org/showthread.php?t=1460604](http://ubuntuforums.org/showthread.php?t=1460604)

I have a eeepc netbook with 4 gig internal flash storage, no hard drive.

I broke the GUI. The ONLY way I can access it now is through a terminal.

It has barely enough space to get the ubuntu .iso image over to it.

I have tried upwards of 10 times with 2 or 3 different distros to make a bootable usb drive with my macintosh. The process appears to complete without errors but the usb sticks are 100% unbootable every time (i.e. the netbook refuses to boot from them, as does my mac).

I get the SAME result using the SAME usb stick that I originally used to install ubuntu on the netbook, so I know it did work once.

Regardless, I would like to try as a last hope to start from scratch making the bootable usb stick from my actual netbook.

I do NOT have access to a GUI (see above). Can you please direct me to instructions to make a bootable usb drive from ubuntu 8.something?

---

### Post by damphoud on 2011-01-04
Need to find out how to use usb-creator via the terminal.

I have to head out for a bit, but when I return, I'll try to find out some more...

---

### Post by C.S.Cameron on 2011-01-04
MultiBootUSB script works from the terminal:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by trevorbsmith on 2011-01-04
> **C.S.Cameron said:**
> MultiBootUSB script works from the terminal:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

No joy. Grub2 is not installed on my netbook and grub2 is required by MultiBoot USB.

---

### Post by trevorbsmith on 2011-01-22
I installed grub2 on my netbook.

I tried Multiboot with both the latest ubuntu netbook remix and with lubuntu. Both produce errors.

Both result in an unbootable USB stick. No grub menu, no boot menu, no boot, no nothing.

I'm just stunned how hard this is. I have literally been trying since last April to reinstall linux on this netbook with 100% failure.

Is it completely impossible to create a bootable flash drive from:

1) a Mac OS X terminal; or
2) a ubuntu 8.something terminal?

BTW, every time I follow the official ubuntu instructions to make the bootable flash drive:

[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)
(step 2)

the flash drive gets set to guid partition table. I assume that's what's causing the problem, but bizarrely it won't book my Mac Mini EITHER, and you'd think that a Mac could understand a guid partition table.

Anyway, I can't install anything from ubuntu's terminal using Multibook either. Baffling.

---

### Post by b0b138 on 2011-01-22
try this

[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

---

