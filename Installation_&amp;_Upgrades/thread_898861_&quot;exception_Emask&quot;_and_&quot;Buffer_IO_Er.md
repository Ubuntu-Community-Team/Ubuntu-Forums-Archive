---
title: "&quot;exception Emask&quot; and &quot;Buffer I/O Error&quot;"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by nautikal on 2008-08-23
When I try to run the live CD or install Ubuntu on two different C2D P35 chipset computers, I get the following screen after the screen with the Ubuntu loading bar (see below). I've tried both the 64-bit and x86 builds, two different CD burners, burning to DVD instead of CD, and two different CD drives. It works fine on my Athlon XP computer. The only things I can think of are a conflict with the P35 chipset or SATA CD drives (as opposed to IDE). Any ideas? 

[img]http://img58.imageshack.us/img58/2538/dsc00789xt0.jpg[/img]
I'm pretty sure ata2.00 is referring to my CD drive, because that changed to ata4.00 when I moved the CD drive's sata cable to a different port.

---

### Post by Partyboi2 on 2008-08-23
>  Buffer I/O error on device fd0, logical block 0 Refers to the floppy drive. Try disabling the floppy drive in your bios or try adding ```
nofloppy 
```or ```
all_generic_ide
``` as a boot option. You can do this by pressing F6 at the main menu and adding it to the end of the line. If none of these work you can try installing with the [[COLOR=Blue]alternate cd[/COLOR]]("http://releases.ubuntu.com/8.04.1/") which has worked for some who have had this error.

---

### Post by Rocket2DMn on 2008-08-23
all_generic_ide may cut it, otherwise try using the irqpoll option with the kernel.

---

