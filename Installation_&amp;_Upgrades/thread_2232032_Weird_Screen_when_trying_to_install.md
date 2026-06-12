---
title: "Weird Screen when trying to install"
date: 2014-06-29
forum: Installation &amp; Upgrades
---

### Post by michael184 on 2014-06-29
Whenever I either select "try ubuntu without installing" or "install ubuntu" I get this weird looking screen that pops up:

[IMG]http://i58.tinypic.com/2zq7vc0.jpg[/IMG]

I am not able to do anything, it just sits there. 

It's Ubuntu 14.04 Desktop 64 bit and I am using a bootable USB stick to install.

Specs:
i7-2600k
2x R9 280X in Crossfire
64GB SSD and 1 TB 10k RPM SATA Drive
MSI P67A-G43 Motherboard

---

### Post by sammiev on 2014-06-29
On boot up look for options and select "nomodeset"

---

### Post by grahammechanical on 2014-06-29
Hi,

1) at the first purple screen with the icons of a keyboard and a human press Enter
2) at the next screen select the language (default is English) and press Enter
3) at the underlying screen that has options to Try Ubuntu or Install Ubuntu press F6
4) a small menu will appear at the bottom right of the screen select nomodeset and press Enter
5) press Esc to get back to the Try - Install screen. Select one or the other of the options and press Enter

See what happens. The live session will run without setting a mode for the monitor screen resolution. There are other F6 options. sometimes we may need a combination of those options to get a live session to load. It all depends upon our hardware.

Regards.

---

