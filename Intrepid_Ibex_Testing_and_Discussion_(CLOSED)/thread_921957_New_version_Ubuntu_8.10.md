---
title: "New version Ubuntu 8.10"
date: 2008-09-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by chanfle on 2008-09-16
hello all....
I concerned....anybody know if the new version 8.10 fix the ACPI issues..???
I have this problem since ubuntu 8.04...

I waiting your response....

Regards...

---

### Post by inportb on 2008-09-17
specifically, which acpi issues are you interested in?

---

### Post by Nullack on 2008-09-17
How about you test it yourself to see? :)

---

### Post by manishtech on 2008-09-17
You facing problems in sleep? or Hibernate or Shutdown?

---

### Post by olskar on 2008-09-17
> **manishtech said:**
> You facing problems in sleep? 

Yes, I'm having terrible nightmares!

Sorry, I couldn't resist 8-[

---

### Post by manishtech on 2008-09-17
> **olskar said:**
> Yes, I'm having terrible nightmares!

Sorry, I couldn't resist 8-[

Go and have sleeping pills... :)

Sorry, I couldn't resist 8-[

---

### Post by joske on 2008-09-17
suspend resume works for me on intrepid, but after resume, acpid is racing like crazy. Not fixed with latest updates.

---

### Post by MALEADt on 2008-09-17
Suspend works, but massively breaks other stuff (Compiz loses it's transparency, WPA fails to connect, ...).

---

### Post by chanfle on 2008-09-17
hello all....
my problem with acpi is when the install the ubuntu...i need modifie the grub...
i have laptop acer amd turion 2.2ghz, when try install appear "bios bug found...."
this is my issue....

regards...

---

### Post by olskar on 2008-09-17
Is it something like MP-BIOS Bug : 8254 timer not connected to I0-APIC?

I get that, but it boots anyway:)

---

### Post by inportb on 2008-09-17
> **olskar said:**
> Is it something like MP-BIOS Bug : 8254 timer not connected to I0-APIC?

I get that, but it boots anyway:)

Indeed... I've been booting with that for ages. At one point, I tweaked the kernel options to get rid of it, but realized that there was no point in doing so.

---

### Post by bpl07 on 2008-09-17
> **olskar said:**
> Is it something like MP-BIOS Bug : 8254 timer not connected to I0-APIC?

I get that, but it boots anyway:)

If you check dmesg, it's actually fixed now with the new kernel by rerouting through 8259A:

> [    0.416026] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.416026] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.416026] ..... (found apic 0 pin 0) ...
[    0.458170] ....... works.

---

