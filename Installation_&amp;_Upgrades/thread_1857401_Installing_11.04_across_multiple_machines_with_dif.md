---
title: "Installing 11.04 across multiple machines with different hardware"
date: 2011-10-10
forum: Installation &amp; Upgrades
---

### Post by Floore on 2011-10-10
Hi there,

I'm all new to deployment of Ubuntu, or any OS for that matter.

I am looking to deploy Ubuntu across multiple machines. There are only a few, probably less than 10, but they will all have different hardware. The company I am doing this for use the rdeploy technology (not fully using rdeploy, just the technology on USB dongles).

I have a pre-configured installation on one machine and I need to image this and deploy it across the machines. Is it likely I will run into lack of drivers for hardware? I don't know exactly how good Ubuntu is with coping with drivers, or if it is better suited to old/new hardware.

Any help on these issues would be greatly appreciated.

Regards,

Floore

---

### Post by collisionystm on 2011-10-10
> **Floore said:**
> Hi there,

I'm all new to deployment of Ubuntu, or any OS for that matter.

I am looking to deploy Ubuntu across multiple machines. There are only a few, probably less than 10, but they will all have different hardware. The company I am doing this for use the rdeploy technology (not fully using rdeploy, just the technology on USB dongles).

I have a pre-configured installation on one machine and I need to image this and deploy it across the machines. Is it likely I will run into lack of drivers for hardware? I don't know exactly how good Ubuntu is with coping with drivers, or if it is better suited to old/new hardware.

Any help on these issues would be greatly appreciated.

Regards,

Floore

Use clonezilla. 

As long as you did not install any custom driver packages on your  source machine, you should not have any problems. If you for instance installed an nvidia driver, you will probably have issues because the xorg you are using is now set to fire up with that driver. You will have to reverse this on all your machines. If it is just a plain vanilla, ubuntu will always automatically choose the best driver that it has.

---

