---
title: "modprobe problem on boot"
date: 2004-10-28
forum: Installation &amp; Upgrades
---

### Post by paulle on 2004-10-28
hello, when booting ubuntu, the boot screen tells me:

modprobe: Fatal: error inserting shpchp (/lib/modules.2.6.8.1-3-386/rs/pci/hotplug/pciehp.ko)

and i can't get my usb-stick to work.
i've a laptop dell inspiron 4000, 128mb ram.

any idea how to resolve this problem, i'm new to ubuntu and linux.

greetings  chris

---

### Post by gallifante on 2004-10-28
....well i've got the same problem....
it says..

modprobe: Fatal: error inserting shpchp  (/lib/modules.2.6.8.1-3-386/rs/pci/hotplug/pciehp.ko) operation not permitted

and...

modprobe: Fatal: error inserting pciehp
(/lib/modules.2.6.8.1-3-386/rs/pci/hotplug/pciehp.ko) operation not permitted

i've got a AMD900 in a VIA KT-133 made by asus.

thanks..

---

### Post by FLeiXiuS on 2004-10-28
I've have had the same thing and I have just ignored it by now.  I believe its a bug in the fixing process right now.

---

### Post by kastorff on 2004-10-28
[QUOTE=gallifante]
modprobe: Fatal: error inserting shpchp  (/lib/modules.2.6.8.1-3-386/rs/pci/hotplug/pciehp.ko) operation not permitted

and...

modprobe: Fatal: error inserting pciehp
(/lib/modules.2.6.8.1-3-386/rs/pci/hotplug/pciehp.ko) operation not permitted

i've got a AMD900 in a VIA KT-133 made by asus.[/QUOTE]

Me too, with the same motherboard and a AMD Athlon 2400+. I've been ignoring it too, but every other boot or so the system will hang after the second error. The next thing that comes up is the network card activation, so I'm not sure where exactly the problem lies. I've configured the card with DHCP and then with a static IP address, and the card works fine when the system boots, so I suspect it's the other errors causing the problem.

---

### Post by jdong on 2004-10-28
pciehp: PCI Express Hotplug.

Unless you're really rich and/or spoiled, this module shouldn't detect any supported hardware  :mrgreen:  :mrgreen:

---

### Post by gallifante on 2004-10-29
yes i continue starting and my pc works fine, also the ethernet card.i configure it for ip, i dont use DHCP.

yeah, ....if my mobo could have PCI-X....( for jdong) :-)

thanks

---

### Post by WOB on 2004-11-07
:-k 
MSI K7T Pro2 main board,
900 AMD Prozessor
I have the same problem: error inserting pciehp and shpchp
USB Camera works
USB printer Epson C40UX does not work.

---

### Post by modonovan on 2004-11-20
Installed Ubuntu the other night and had a bit of an issue with my Video card ( Geforce4 MX 440 ) which I fixed in a round about way. Firstly, i swapped out my card for me old voodoo 3 card and that worked fine. rebooted with my new card and configured it manually to use the nv driver...happy days. boot up this morning to find these errors as above but my system freezes _every_ boot. 

Any ideas on what i need to do to fix this?

---

### Post by smue on 2005-02-06
Hi!
I had the same problem, but "McWhirter" told me, how to fix it ;) Have a look here...
[Mc Wirther](http://craige.mcwhirter.com.au/2005/ubuntu-dell-4700.html) 

```

Hotplug Errors on Boot after Installation

When you reboot after a successfull install you will notice the following five lines:

modprobe: FATAL: Error inserting pciehp (/lib/modules/2.6.8.1-4-686/kernel/drivers/hotplug/pciehp.ko) Operation not permitted
modprobe: FATAL: Error inserting shpchp (/lib/modules/2.6.8.1-4-686/kernel/drivers/hotplug/shpchp.ko) Operation not permitted
modprobe: FATAL: Error inserting pciehp (/lib/modules/2.6.8.1-4-686/kernel/drivers/hotplug/pciehp.ko) Operation not permitted
modprobe: FATAL: Error inserting shpchp (/lib/modules/2.6.8.1-4-686/kernel/drivers/hotplug/shpchp.ko) Operation not permitted
modprobe: FATAL: Error inserting hw_random (/lib/modules/2.6.8.1-4-686/kernel/drivers/char/hw_random.ko) No such device

Fear not! There is nothing fatal about this at all. To stop hotplug trying to load drivers it has no business trying to load (on this system, anyway) add the following three lines to the bottom of /etc/hotplug/blacklist

# Not loading on boot. Removed from sight :)
pciehp
shpchp
hw_random

Next time you boot you'll notice those annoying messages are now gone. I'd rather know why they won't load but haven't had time to work that out yet so removing them from sight will do for now. 

``` 

Gretz,
SMü

---

