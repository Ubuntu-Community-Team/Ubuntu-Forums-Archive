---
title: "Quick check on effects of a no-acpi install"
date: 2005-10-04
forum: Installation &amp; Upgrades
---

### Post by MGajh on 2005-10-04
I have an Acer Aspire 1360 laptop (AMD Sempron) that I have tried various distros (Suse 9.3, 10.0 RC1, Foresight .9.0). If I do a standard install, I get all sorts of problems such as USB 2.0 devices failing to mount (unless plugged into a USB 1 hub first, onboard wireless unable to function, Netgear WG511T pcmcia wireless lan same).

Time therefore to try another distro and I figure with such a big forum community, Ubuntu had to be the one to go for. So.....

If I do a no-acpi install I can at least get USB and the PCMCIA card working (onboard wireless no but I think that was down to the wireless tools and ndiswrapper version I was using).

Ideally, I'd like to get acpi enabled - can anyone suggest why linux is having such difficulty with my laptop and is there a way of fixing it after install? In the event that I have to go with a no-acpi install, does anyone know if that will prevent the onboard wireless card from working - I've noticed on a couple of boards that to enable the special function keys on the laptop, there is a downloadable app that changes the acpi config to enable it to control the card therefore if acpi is disabled is the card also?

Hope you can help - I've been working on this for weeks!!

---

### Post by darkmatter on 2005-10-04
What does that laptop have for a BIOS? Mobo specs?

---

### Post by MGajh on 2005-10-04
[QUOTE=darkmatter]What does that laptop have for a BIOS? Mobo specs?[/QUOTE]

Hi!

Sorry for the delay.

Motherboard is a VIA K8N800 and bios is Phoenix 4.0 Release 6 using Acer's current v1.09.

Thanks

Andy

---

### Post by darkmatter on 2005-10-04
[QUOTE=MGajh]Hi!
Sorry for the delay.
Motherboard is a VIA K8N800 and bios is Phoenix 4.0 Release 6 using Acer's current v1.09.
Thanks
Andy[/QUOTE]

I'll try to dig up some info on that board regarding acpi under linux.

---

### Post by MGajh on 2005-10-04
[QUOTE=darkmatter]I'll try to dig up some info on that board regarding acpi under linux.[/QUOTE]

Thanks for the help but guess what....

I've just installed Breezy Badger through a standard install and everything seems to work. My USB 2 memory stick is working the Netgear PCMCIA card is in, configured and downloading updates as we speak. I haven't time to fiddle with the onboard Wireless at the moment but I'll play with that later and post seperately if need be.

Ubuntu rocks!

---

### Post by darkmatter on 2005-10-04
Yep. Breezy is awesome. A major improvement over Hoary.

Glad you got everything working.:)

---

### Post by Noobie1982 on 2007-10-23
Quick check, if I install with pci=noacpi, would that explain why my on board wireless card doesn't work?  Just a thought, since syslog seemed to think it was an IRQ problem, and as I understand it pci=noacpi should disable IRQ on pci devices.

---

