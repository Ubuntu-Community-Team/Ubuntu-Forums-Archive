---
title: "Can't start install on live cd"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by hobojoe2k1 on 2008-06-03
When I run the 8.04 live cd, it gets me to the initial menu.  When I choose install, it initiates the kernel, shows the ubuntu screen for a few seconds, then displays:

"udevd-event [1583]: run_program: '/sbin/modprobe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)"

I md5summed the iso image and everything worked out fine.  I have also tried burning the image on two different cds and got identical results.

I am running a 2.1ghz intel core duo processor and I have 3gb of ram.  The iso is "ubuntu-8.04-desktop-i386.iso"

Anyone have any ideas?

---

### Post by Partyboi2 on 2008-06-03
See what happens when you add all_generic_ide as a boot option. When you are at the main menu, press F6 to add boot options and add ```
all_generic_ide
```  and then press enter.

---

### Post by SonicSteve on 2008-06-04
> **Partyboi2 said:**
> See what happens when you add all_generic_ide as a boot option. When you are at the main menu, press F6 to add boot options and add ```
all_generic_ide
```  and then press enter.

Forgive me I know I'm not the OP but I have the same problem and using all_generic_ide didn't help. I've seen this error a few times now both on 4 year old hardware and new hardware.

---

### Post by wolfen69 on 2008-06-04
i find using the alternate install cd fixes this.

---

