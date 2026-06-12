---
title: "How do I re-install my system without loosing apps?"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by Anagonda on 2007-05-08
Hi,

Is  there anyway to run a "re-install" to my system?
I changed my cpu, motherboard and gpu. So my ubuntu hangs on boot. Grub goes fine, then I get a few usb errors and nothing. I only waited about 5minutes, but it didn't boot, few more usb errors came to the screen.

I don't want to wipe my hole system. I have fully working E16, E17, Gnome and KDE on the box. So it would be to much work to get everything to work nice again. I have a separated /home, but it doesn't make the E17 installation any easier.

So any help? Does the alternative cd have any kind of "update"? Or any way to install new system over the old one so that the window managers would still work?

---

### Post by Anagonda on 2007-05-09
Ok, system is running fine.

The 2.6.20-15-386 kernel didn't like my motherboard. I got the system booted by adding irqpoll to boot parameters in grub. I changed the kernel to generic and now all works fine(I dont need the irqpoll anymore) except network(thats an abit AB9 problem). But I had a spare 3com network card so I fixed the problem the easy way.

---

