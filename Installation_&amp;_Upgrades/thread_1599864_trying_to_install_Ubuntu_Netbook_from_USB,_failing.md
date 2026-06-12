---
title: "trying to install Ubuntu Netbook from USB, failing"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by EllieMurasaki on 2010-10-18
I have an Asus Eee running the factory installation of Linux. Xandros, I think. Whatever it is, it's not letting me update Firefox, so I'm trying to replace it with Ubuntu Netbook. I made a bootable USB stick according to the instructions at [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download), and I know the problem isn't with the USB because the Windows machine I'm currently on wants to know if I want to try out Ubuntu or install Ubuntu or learn more, but when I put the stick in the netbook, nothing happens, and when I reboot with the stick in the netbook, nothing happens. The netbook's set to boot from a USB if there's one present; I checked. Is the problem that the stick's only supposed to work on Windows? If so, how do I fix it? If not, is this something I should go harass the appropriate segment of the Linux community about? If not, wtf is wrong and what do I do?

---

### Post by snowpine on 2010-10-18
You need to choose the correct options in your EEE's bios to boot from the USB stick. Not knowing which model EEE you have, I can only guess :) but on my EEE 900ha there was an option called "boot booster" or something that I had to disable before I could boot from the USB. Then, I was able to press the Esc key at startup to choose the USB.

A great resource for EEE questions: [http://forum.eeeuser.com](http://forum.eeeuser.com)

---

### Post by EllieMurasaki on 2010-10-18
It's a 900, and I don't know what this boot booster thing is. I'm looking at the BIOS setup thing, boot device priority screen, and it swears first is Removable Dev., second HDD:SM-ASUS-PHISON.

---

### Post by C.S.Cameron on 2010-10-18
With my daughters EEE you need to select the flash drive under Hard Disk Drives. Not Removable Drive.

---

### Post by EllieMurasaki on 2010-10-18
My choices are Removable Dev., HDD:SM-ASUS-PHISON SSD, ATAPI CD-ROM, and Disabled. And I found the boot booster and it is already disabled.

---

### Post by snowpine on 2010-10-18
What happens when you reboot and press 'Esc' at the BIOS "splash" screen?

---

### Post by EllieMurasaki on 2010-10-18
...asks whether I'm booting from the USB. I feel stupid now. Thanks!

---

