---
title: "Lucid as KVM guest under Karmic"
date: 2010-02-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bmullan on 2010-02-27
I tried installing latest Lucid (alpha 3) Desktop as a KVM 64 bit guest running on my Karmic 64 bit system.

I'm not quite sure where to point to issues but just doing the installation from an ISO file there are graphics oddities occurring.  

Once KVM guest Lucid was installed and rebooted.. 
reboot seemed really slow again with graphics oddities occurring.

After 4-5 min I still didn't have any menu on the desktop?   
At that point I figured it might be good to ask if anyone else has tested it this way yet?

My host machine
mobo: gigabyte ga-ma78gm0s2h
cpu amd x940 quad cpu 3ghz
memory: 8g ddr2
drives: SATA drives

---

### Post by xebian on 2010-02-27
> **bmullan said:**
> I tried installing latest Lucid (alpha 3) Desktop as a KVM 64 bit guest running on my Karmic 64 bit system.

I'm not quite sure where to point to issues but just doing the installation from an ISO file there are graphics oddities occurring.  

Once KVM guest Lucid was installed and rebooted.. 
reboot seemed really slow again with graphics oddities occurring.

After 4-5 min I still didn't have any menu on the desktop?   
At that point I figured it might be good to ask if anyone else has tested it this way yet?

My host machine
mobo: gigabyte ga-ma78gm0s2h
cpu amd x940 quad cpu 3ghz
memory: 8g ddr2
drives: SATA drives

May I suggest virtualbox from virtualbox.org?  It's by far the easiest/best virtualizer IMO.

---

### Post by Ibidem on 2010-02-27
@xebian:
It seems Lucid stopped booting in VirtualBox right around Alpha2.
(per my own experiences, and per Jaxx)
IIRC, Qemu worked.  That's in the same package as kvm.
Ibidem

---

