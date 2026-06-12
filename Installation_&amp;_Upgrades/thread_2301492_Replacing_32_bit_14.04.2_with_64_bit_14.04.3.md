---
title: "Replacing 32 bit 14.04.2 with 64 bit 14.04.3"
date: 2015-11-02
forum: Installation &amp; Upgrades
---

### Post by jrh74 on 2015-11-02
First, thankyou "deadflowr" for your help in response to my recent question "ubuntu modificatinsbefore installing MythTV".  At this time i have downloaded 62 bit 14.04.3 and have made a bootable USB drive using startup disk creator.  Since it is my understanding that I can't uninstall my current operating system (32 bit 14.04.2), I assume this means I must boot from the USB drive to install the new OS and this will somehow overwrite the existing one.  Is this so?  How do I change the boot order so that booting is from the USB drive?

---

### Post by ian-weisser on 2015-11-02
> **jrh74 said:**
> I must boot from the USB drive to install the new OS and this will somehow overwrite the existing one.  Is this so?
Correct. Once you boot form the USB, overwriting the existing install is one of the options.
Er, one assumes you haven't set up complex stuff like dual-booting nor LVM. If you have, now is the time to say so....

> **jrh74 said:**
> How do I change the boot order so that booting is from the USB drive?
Use your machine's boot options, usually displayed at poweron along with the manufacturer's logo  ('Press F12 for options')

---

