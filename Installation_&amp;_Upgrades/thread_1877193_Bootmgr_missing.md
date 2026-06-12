---
title: "Bootmgr missing"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by Lupajz on 2011-11-07
Hey guys I got this trivial problem, but I find myself unable to solve it :/ 

I am running 10.10/W7 with grub manager. I can boot into any of those OS without problem. But problem occurs when I stick bootable USB with 10.04 into machine. It says bootmgr is missing and gives me only option to restart book. Beside that if I dont stick USB in it works fine ;) I get that table where I can choose OS from HDD.

Solutions or tips or anything ? :popcorn:

---

### Post by oldfred on 2011-11-09
Bootmgr missing is a Windows error.

Is your BIOS set to boot USB first? Does bootable USB have grub2's boot loader or a Windows boot loader.

A few BIOS will give a boot error if there is not a boot flag on a primary partition, but that is usually just a not bootable message. Grub does not need boot flag.

---

