---
title: "Problem with instalation"
date: 2005-05-28
forum: Installation &amp; Upgrades
---

### Post by nick79 on 2005-05-28
I try to install Ubuntu. After the firs screen when I hit enter for normal instalation I gor a few mesages and the last one is something like this:
"Uncompresing linux ... Boot kernel"
and after that nothing's gonna happend.
Same thing with Knopix 3.8, Beatrix 2005.1.
I try with no acpi options, server instalation, but nothing.

I have: AthlonXP 2000, 512MB ram, 2 x Maxtor hdd, ATI Radeon 9000 Pro, Creative Live 5.1, Pinnacle Pctv, Asus Via KT 400 motherboard, onboard integrated sound card  disabled in BIOS.
The interesting thing that i could run Knoppix (some earlier version) on this computer.

Could anyone help mewith this issue?
Thanks in advance.

---

### Post by stevenyu on 2005-05-29
sounds like your computer doesn't like the 2.6 kernel, maybe you have try to run Debian

---

### Post by wallijonn on 2005-05-29
The only hardware which might not be supported is the Pinnacle PC TV card. You'll have to check the hardware compatibility list, elsewhere.

I would pull that card out and try again.

---

### Post by nick79 on 2005-05-29
[QUOTE=stevenyu]sounds like your computer doesn't like the 2.6 kernel, maybe you have try to run Debian[/QUOTE]

I don't think so because I allready instal some distros with that kernel.

Pinnacle it is not a problem because I try to install without this card, but I dont have any success.

Anyway thanks for sugestions.

---

### Post by wallijonn on 2005-05-29
Are you only installing the 'server' version? Did you try to install Warty? Are you using SATA drives? Do you have a wireless card installed? Are you using a wireless mouse? 

It could be something simple, like manually assigning your IRQs in the BIOS.

---

### Post by nick79 on 2005-05-29
[QUOTE=wallijonn]Are you only installing the 'server' version? Did you try to install Warty? Are you using SATA drives? Do you have a wireless card installed? Are you using a wireless mouse? 

It could be something simple, like manually assigning your IRQs in the BIOS.[/QUOTE]

I try to instal server and "normal" insatalation. No I didn't try to install Warty, only Hoary. I don't have sata drives and I don't have wireless card. Yes, I'm using wireless mouse but I don't believe that it is problem.
I dont know how to  manually assign IRQs in the BIOS. Is that affect my windows XP instalation?

Anyway thanks.

---

### Post by nick79 on 2005-05-30
Does anyone can figure what is problem or the only thing what can I do is to buy a new computer.

---

### Post by mingus on 2005-05-31
A few things to try:

Install the desktop version instead to see if the kernel will load.

Using kernel boot arguments to change how irq's are assigned.  For example, noapic, or pci=nobios.  There are others.

Disable all power management:  noacpi, acpi=off, pci=noacpi

Where you are getting the error is also close to when the framebuffer is loaded.  This could be an issue with your Radeon card until you can later load a driver specific to it.  Try vga=0x301 or vga=normal.

--mingus

---

