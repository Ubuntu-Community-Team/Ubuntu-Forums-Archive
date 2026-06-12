---
title: "Weird installation problem."
date: 2005-06-16
forum: Installation &amp; Upgrades
---

### Post by afonic on 2005-06-16
Hi there, 

I have a pretty weird installation problem. Let me start with my system:

Athlon64 3000+
Chaintech VNF4 Ultra (nForce4 Ultra)
200GB Seagate SATA
Asus GeForce 6600GT PCI Express

So I start the install of a Hoary 5.04 64bit system. The CD boots, the stuff are loaded in the memory, until one spot:
When it says "Trying to enable the frame buffer" it stays there for ~1 minute and then loading the install GUI VERY slow. Like One-one line filling gray and then all over again to turn blue.
The language selection dialog appears and it all stops there.

I tried many stuff, like removing all unnessesary devices, using a 80GB PATA drive etc but the same thing happens all the time.
I have a x86 version of Ubuntu which I successfully installed in my laptop and it does exactly the same thing too, so it's not the CD or the 64 version but my system.
I tried installing Ubuntu in a VMware virtual machine running on the windows I have in the first drive and it run just fine!
I think the PCI Express card might be it, but I don't have a plain PCI one to try.

Any ideas / hints ?

Thx....

---

### Post by alastair on 2005-06-16
No real idea.

You could try booting with a framebuffer option like :

linux vga=791

but I am not sure if this would help.

---

### Post by afonic on 2005-06-16
[QUOTE=alastair]No real idea.

You could try booting with a framebuffer option like :

linux vga=791

but I am not sure if this would help.[/QUOTE]
 Hi,

thanks for the reply. If I do that I don't see anything on the screen except a small grenn line on the top left corner. I tried the laptop option too (even thought it's desktop) but no worky.

Do you know a list of framebuffer options? Maybe I can try some more.

---

### Post by afonic on 2005-06-16
Write cancel on that. I disabled frame buffer (shame on me I didn't notice the option), and still nothing.

As soon as the first dialog comes up, everything freezes.

---

### Post by afonic on 2005-06-17
I just tried Debian and everything work just fine.

The problem with Ubuntu goes on. Debian shows language selection in 10secs, Ubuntu needs 5mins and then freezes. Anyone having any idea what may be it?

---

### Post by afonic on 2005-06-18
After many tests I found the right boot command:

boot: linux acpi=off noapic nolapic

---

