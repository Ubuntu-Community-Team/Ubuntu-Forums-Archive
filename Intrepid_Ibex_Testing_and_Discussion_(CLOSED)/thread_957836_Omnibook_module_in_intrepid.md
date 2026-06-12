---
title: "Omnibook module in intrepid?"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by amrlima on 2008-10-24
Does anyone know if the omnibook kernel module is included in intrepid's kernel? It solves some issues with some laptops (acpi and bluetooth). There are open bugs in launchpad but not much life there for some time...

---

### Post by Yellow Pasque on 2008-10-24
sudo modprobe omnibook fails and I searched for omnibook.ko and didn't come up with anything.
I would take that as a no. You'll need to compile the source.

EDIT: Here's the Launchpad bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/45021](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/45021) . I posted the procedure to build the module from source in that bug report.

---

### Post by amrlima on 2008-10-26
Too bad it's not in intrepid. I'll try to compile the module if my bluetooth still doesn't work when I'll make the upgrade.

Thanks!

---

