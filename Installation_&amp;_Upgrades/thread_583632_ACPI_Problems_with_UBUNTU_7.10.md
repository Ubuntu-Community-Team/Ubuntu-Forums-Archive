---
title: "ACPI Problems with UBUNTU 7.10"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by nightcrawl on 2007-10-20
Hi there!

Ive searched a lot to solve my problem but i've encountered nothing similar.

The fact is, when i've installed my 7.10 copy, just after the boot screen, the system black's out. If i turn acpi=off, he runs cool.

When i get it installed the same problem happens after the grub screen. I i turn acpi=off, he runs again.

I could simply turn acpi=off in the grup config files, but the fact is, i want it on, for the battery management and special keys.

Someone know's how to solve it?

My laptop is an ASUS m3n.

Thanks

---

### Post by nightcrawl on 2007-10-21
Anyone? :confused:

I've noticed that the same problem happens with the 7.04 version, so i'll have to go back to 6.10 to get Ubuntu work.

If anyone knows how to solve the problem please tell me :(

---

### Post by msvr on 2007-10-21
Hi
Me too.
I am also facing exactly the same problem on my desktop.
Does any one know of any solution?

Thanks.
Vijay

---

### Post by nightcrawl on 2007-10-21
I'm upgrading the kernel to 2.6.23.1 without the new Power Management support of ACPI... i dont belive that will work, because i belive in a confilte betwen the PATA drivers and ACPI, and i'm not sure how to deactivate in the kernel opt. 

But i'll say when this ends...

---

### Post by erv2 on 2007-10-22
my situation is even worse, i have windows xp and 7.10 dual boot.

7.10 wont run unless i set acpi=off AND set acpi disabled from bios. 

windows xp wont run unless i set acpi enable from bios.

so every time i change OS from boot, it's not just choosing different options from grub, i have to go into the bios and change the acpi setting.

it's just annoying.:confused:

---

### Post by nightcrawl on 2008-05-23
Problem solved in UBUNTU 8.04

---

