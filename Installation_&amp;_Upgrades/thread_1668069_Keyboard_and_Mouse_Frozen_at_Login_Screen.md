---
title: "Keyboard and Mouse Frozen at Login Screen"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by nonexplosive on 2011-01-15
Hi everybody.

I let the update manager run overnight on my netbook because it was taking a while. When I woke up, my netbook was off. It may have shut off during the updates. Now, when I turn it on, it gets to the login screen but the keyboard and mouse don't work. Is there anything I can do without a Live CD? Unfortunately I don't have a flash drive or anything with me.

Thanks in advance.

---

### Post by fuzzyworbles on 2011-01-15
the best means to diagnose would be to use another computer to either A) ssh into the machine and check dmesg, B) to make a live usb to do the same. or C) just boot using recovery mode (if ubuntu is the only OS you have installed, the grub menu is hidden. hold down shift while booting to get the menu). C is probably all you've got if you seriously don't have 2 bucks for a USB stick and access to another computer.

once you've got a console, check dmesg for errors. if the upgrade was interrupted, you can resume it in the recovery console. search this forum or just google for how to initiate a wireless connection with iwconfig. if you've got a wired connection, it's as easy as running the dhcpd client.

---

