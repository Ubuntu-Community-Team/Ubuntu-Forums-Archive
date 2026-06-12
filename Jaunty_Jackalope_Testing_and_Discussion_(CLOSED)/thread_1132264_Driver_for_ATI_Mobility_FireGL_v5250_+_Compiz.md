---
title: "Driver for ATI Mobility FireGL v5250 + Compiz"
date: 2009-04-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ecl7 on 2009-04-21
Hi!

I'm new to Ubuntu, and I've been trying out Ubuntu 9.04 RC on my laptop.  I'm trying to get compiz to work, but I can't seem to install the proprietary driver for my ATI video card successfully.  When I installed the ATI Binary Driver and the ATI Catalyst Control Center from the "add/remove applications" manager, Ubuntu just crashed upon reload and would not start the graphical environment.

I've looked all over the forum for a solution, but can't seem to find one.  Does anyone know how to make this work?  Can someone show me how to install the driver and enable compiz?

I have a Lenovo Thinkpad T60p with an ATI Mobility FireGL v5250 video card.

Thanks so much!

---

### Post by barisurum on 2009-04-21
Are you using the 9.4 proprietary driver from ati? If not any driver below 9.4 doesn't have support for the new xorg included in 9.04. I'm not sure this driver (9.4) has support for your card, but if it has then I suggest downloading it from ati and installing manually.

---

### Post by alphacrucis2 on 2009-04-21
> **ecl7 said:**
> Hi!

I'm new to Ubuntu, and I've been trying out Ubuntu 9.04 RC on my laptop.  I'm trying to get compiz to work, but I can't seem to install the proprietary driver for my ATI video card successfully.  When I installed the ATI Binary Driver and the ATI Catalyst Control Center from the "add/remove applications" manager, Ubuntu just crashed upon reload and would not start the graphical environment.

I've looked all over the forum for a solution, but can't seem to find one.  Does anyone know how to make this work?  Can someone show me how to install the driver and enable compiz?

I have a Lenovo Thinkpad T60p with an ATI Mobility FireGL v5250 video card.

Thanks so much!

I had a similar problem with the Lenovo T400 with HD3400. Installed the proprietary via Jockey killed X. I managed to fix the problem by doing the following command from the recovery root prompt:

```
aticonfig --initial -f
```

I think the FireGL v5250 is still supported by Catalyst 9.4 so you should be ok as far as that goes.

---

### Post by t.alex on 2009-04-22
> **alphacrucis2 said:**
> I think the FireGL v5250 is still supported by Catalyst 9.4 so you should be ok as far as that goes.

no, it isn't supported any more! Support ended with Catalyst 9.3.

> **ecl7 said:**
> Does anyone know how to make this work?  Can someone show me how to install the driver and enable compiz?

It should work straight away. You don't need the proprietary driver in order to run compiz. Jaunty loads the the "radeon" driver, which has basic 3d support -compiz runs ok with it.

---

### Post by gilsr on 2009-04-22
I have t60p with mobility firegl 5250 and compiz works fine with open driver. Can no longer play Team Fortress tho.  Got the following from "Unofficial ATI linux driver wiki".
MOBILITY FireGL

    Support for these cards are temporarily suspended as of the fglrx driver 8.40.4. 

    * MOBILITY FireGL T2/T2e (4E54)
    * MOBILITY FireGL V3100 (5464)
    * MOBILITY FireGL V3200 (3154)
    * MOBILITY FireGL V5000 (564A, 564B)
    * MOBILITY FireGL V5100 (5D49)
    * MOBILITY FireGL V5200 (M56 71C4)

Hopefully support will come back for these chipsets in a later release.

---

