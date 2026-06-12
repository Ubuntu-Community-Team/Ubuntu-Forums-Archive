---
title: "Wont Install [boot]"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by masonmills on 2011-07-14
So ive been trying to figure this out for about 2-3 hours now....
 
They CD will boot... I pick my language and then When I click Install Ubuntu 11.04.. It kinda liek stall or lags for a second and then it restarts and eventually I get back and try and press enter for install and it just restarts... Very very agravating as It's making it this much harder to come back to Ubuntu.
 
 
Idk what the problem is, I reloaded my BIOS to default. Idk what to do. "Dell Inc. 1.0.3 - Vostro 200" are my BIOS i do belive, some **** like that.
 
 
Please help..

---

### Post by Bucky Ball on 2011-07-14
Try 10.04 LTS and see if you get the same issues. Welcome back.

---

### Post by masonmills on 2011-07-14
Is 10.04 the same kind of boot setup as 11.04, Cause I remember installing a older version for a friend that I showed Ubuntu to.
 
I'm a Unbuntu superdude lol. Yopefully I'll be up and running and off this godforsaken Win7 tonight. :KS

---

### Post by dino99 on 2011-07-14
try disabling acpi stuff on boot line, either: noacpi, nolapic, noapic, nomodeset, irqpoll

---

### Post by Bucky Ball on 2011-07-14
> **masonmills said:**
> Is 10.04 the same kind of boot setup as 11.04 ...

Pretty much. 10.04 uses the Gnome desktop environment, in 11.04 this has been changed to default to Unity DE, but you can choose to use Gnome from the login screen also. The install process is virtually the same though. Disabling stuff on the boot line, as suggested by Dino, might be worth a try also, but hit and miss at this point (unless you research exactly what/if your hardware needs the kernel line changed). 

Easiest way is when you get to the menu options at boot, choose the kernel you want to boot, hit 'e' for edit, find the line that ends with or contains 'quiet splash', leave a space and add some of Dino's suggestions. Start with 'acpi=off'. If that works, let us know and we can show you how to make the change permanent.

---

