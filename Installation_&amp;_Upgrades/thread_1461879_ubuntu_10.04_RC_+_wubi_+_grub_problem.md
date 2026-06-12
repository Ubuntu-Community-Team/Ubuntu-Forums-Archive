---
title: "ubuntu 10.04 RC + wubi + grub problem"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by Martijnvdc on 2010-04-24
- I installed ubuntu 9.10 using wubi
- I upgraded ubuntu 9.10 to 10.04 RC
-> now i can't boot ubuntu, not even the grub menu comes up.
The grub menu shows something about "file not found" and quickly reboots (hard for me to read what's there)

How can i fix grub so that i get the list of OSes again?
(sorry for my bad english, not my native language)

thanks in advance :p

---

### Post by Kljuka on 2010-04-24
Hmm...
Your grub configuration might be false.
You'll probably need CD to repair it (try Ubuntu option).

---

### Post by Kljuka on 2010-04-24
Grub is located in /boot/grub
I would check /boot/grub/menu.lst file (it's configuration)

---

### Post by Martijnvdc on 2010-04-25
C:\ubuntu\disks\boot\grub
is empty. Is this normal?

I tried fixing it from withing a live cd.
But i can't just do: 
grub > root (hdX,Y)Because ubuntu is installed on 2 disks in raid0...

any idea how to get this menu.lst back?

---

### Post by Kljuka on 2010-04-25
To correct myself:

Ubuntu has switched since 9.10 to the newer GRUB 2, which uses /boot/grub/grub.cfg,  although this file is auto-generated; files in /etc/grub.d ultimately  control what goes in /boot/grub/grub.cfg. The grub-mkconfig command  should theoretically auto-detect what OSes you've got on your system and  generate a new configuration file.

If it is a hardware raid, you shouldn't care (because your hardware takes care of RAID and your OS only sees one disk).

---

