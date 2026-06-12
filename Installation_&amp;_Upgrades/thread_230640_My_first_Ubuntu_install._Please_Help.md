---
title: "My first Ubuntu install. Please Help"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by covenant on 2006-08-06
Greetings.
I've downloaded Ubuntu 6.06 today. When I boot Ubuntu if gives me some errors and stops. The errors are:

[SIZE="2"][17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[17179570.824000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.824000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.824000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2[/SIZE]

I have a Acer 1652 laptop with a X300 gfx and 512Mb ram.
I want to start using linux instead of windows, but I'm very noob. I think ubuntu is nice for beginners, but what can I do to boot my computer?
Thank you for all the help you can give.

---

### Post by zxee on 2006-08-06
There is a similar thread here [http://ubuntuforums.org/showthread.php?p=1326651and](http://ubuntuforums.org/showthread.php?p=1326651and) also some hits on > PCI: Cannot allocate resource region 7 of bridgefrom a search but it seems the ubuntu thread doesn't have a resolution as yet. You might try some of the special ways to boot e.g acpi=off or experiment with other boot parameters.

---

### Post by Ocxic on 2006-08-06
check your BIOS and make sure all of you irq, and PCI setting are on auto.

---

