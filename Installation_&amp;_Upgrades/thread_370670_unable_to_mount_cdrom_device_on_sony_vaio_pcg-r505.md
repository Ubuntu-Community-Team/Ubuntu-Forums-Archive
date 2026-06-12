---
title: "unable to mount cdrom device on sony vaio pcg-r505el laptop"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by jogmiers on 2007-02-26
I'm trying to install Edgy on a friend's laptop and keep getting an error when trying to mount the cdrom device. I've tried the live install disc and also text mode and oem installs with the alternative disc; with the live disc i can't even open up the install shortcut on the desktop, the alternative disc fails in oem and text install modes because it can't mount the cdrom device. any suggestions? thanks

---

### Post by Kateikyoushi on 2007-02-26
I have 3 Vaios and ubuntu boots on them without problem, even from the ilink external drive.

Try this boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

### Post by jogmiers on 2007-02-27
got the same error...

---

### Post by jogmiers on 2007-02-27
i tried a knoppix cd just to see if there was a problem with the cdrom. knoppix ran fine...

---

### Post by ssawatzky on 2007-07-08
The solution for this is to change the dev line from cdrom so it reads "/dev/scd0" in case anyone else has this problem.

---

