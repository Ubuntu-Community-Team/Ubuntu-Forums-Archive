---
title: "Problems after updating"
date: 2018-01-05
forum: Installation &amp; Upgrades
---

### Post by purefur on 2018-01-05
I am new with Ubuntu. I was working with SSDs and could accidentally format one of segments of my HDD on the laptop (dell inspiron 15 series). Also I used "sudo apt-get update/upgrade" command. Then i rebooted system. Now Ubuntu doesnt boot and i cant reinstall or fix it. Here is my bios setup and the error [https://imageshack.com/a/FlJl/1](https://imageshack.com/a/FlJl/1)

---

### Post by grahammechanical on 2018-01-05
Do you still get a Grub boot menu? Is it after selecting Ubuntu that you get the kernel panic message? It could be that formatting one of the partitions removed Ubuntu or removed the boot partition or wiped the partition clean.

We need more detailed information. There is a Utility called Boot Repair. We install it in a Live Ubuntu USB stick and then run boot repair. It has an option to create boot info summary. I recommen doing that. Once the summary is created you will be give a URL to a pastebin server where the summary is stored. Put that URL in this thread then we can examine the state of your hard drive. And advise whether to accept the boot repair recommend repair or not.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Regards.

---

