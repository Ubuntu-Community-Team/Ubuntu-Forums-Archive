---
title: "Freeze at updating system"
date: 2009-07-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Marat89 on 2009-07-11
Hey,
I have Problems with Karmic using it in VirtualBox.

When I update the system, i get a freeze.
The System hangs at downloading the main rep. sources.

I have to close the Appliance.

Anybody a idea?

---

### Post by ronacc on 2009-07-11
update-manager hung on me checking for updates this morning , shutting it down and upgrading with synaptic went normal . This is on a regular install not virtualbox .

---

### Post by Marat89 on 2009-07-11
upgrading with synaptic: same issues

---

### Post by FFuser on 2009-07-11
> **Marat89 said:**
> upgrading with synaptic: same issues

If you are using virtualbox 3.0 => their is a bug in Vbox 3.0 which hangs on heavy network load.

It seems you can fix it if you use a Intel Pro network adapter instead of one of the PC-net adapters. (That worked for me)
If you still have problems you better downgrade again to 2.4 or wait for 3.0.1 te be relaesed

---

### Post by Marat89 on 2009-07-11
Thank you.
Upgrading VirtualBox fixed the problem.

---

