---
title: "Problem installing Gutsy"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by wroopy on 2007-12-23
I've problem installing Gutsy.

I've tried to install Server 7.10 x64 (amd64) and i386 version. After choosing to install and "loading linux kernel", the screen goes black and the computer restart.  When trying amd64-version I briefly gets the information ""Kernel direct mapping tables up to 1000000 @ 8000-8b00" before the computer reboots.

I also tried to run the Live CD, both x64 and i386 version with the same problem.

Are there a settings in BIOS that I need to change?
Could I try some boot options?
Could it be hardware problem?  How to find out what components that fails?

**Hardware:**
MB: Gigabyte GA-G33-DS3R (Upgraded to lates BIOS, settings are from optimized defaults)
Minne: 2x2Gb (Muskin 6400) Tried with only one memory and different orders, without any difference
HD: WD RE2 500 Gb
CPU: Intel E6750
SATA-connected DVD

---

### Post by kingcharles1666 on 2007-12-23
Did you make sure the cd's you burned are ok?

---

### Post by wroopy on 2007-12-23
> **kingcharles1666 said:**
> Did you make sure the cd's you burned are ok?

Check CD for defects runs OK ( on another computer with the same drive).
The CD:s works fine on another computer.

---

### Post by Craigus on 2007-12-23
What video hardware does the system have ?

---

### Post by Partyboi2 on 2007-12-23
You could try removing the splash option at boot and see if that works.
At the menu screen press F6 and at the end of the line change "splash" to "nosplash" then press enter.
If that doesn't work then try "nosplash noapic"
If none of those work you could try using the alternate cd to install
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

---

### Post by wroopy on 2007-12-23
> **Craigus said:**
> What video hardware does the system have ?

It is the built in video on the motherboard, i think it is GMA3100(?) I.e. the build in in the G33 chipset.

/Andreas

---

### Post by wroopy on 2007-12-23
> **Partyboi2 said:**
> You could try removing the splash option at boot and see if that works.
At the menu screen press F6 and at the end of the line change "splash" to "nosplash" then press enter.
If that doesn't work then try "nosplash noapic"
If none of those work you could try using the alternate cd to install
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

Alternative CD or nosplash noapic does not work.
Still the same result.
Any other ideas?

---

### Post by wroopy on 2007-12-26
Tried to record the boot with my camcorder and I got some more information;

The last lines on the screen prior to reboot are;
Brought up 2 CPUs
migration_cost=nn


Tried to boot on the CD on another machine and on that machine I got ""Booting paravirtualized kernel on bare hardware" after the lines above.

Could it indicate CPU or motherboard error?

---

### Post by wroopy on 2007-12-27
Got a C2D E6600 to try with and it didn't work either.

I'm going to return the motherboard and hope that the new one will work!

---

### Post by loafimus on 2007-12-27
I'm having the exact same problem.

I'm downloading the 32 bit version right now to see if that corrects it.  Very strange.

---

### Post by KotZer on 2008-01-08
I confirm the problem too, with 2 amd64 cpus. the cd is has no defects and i have tried all the boot options....

> **loafimus said:**
> I'm having the exact same problem.

I'm downloading the 32 bit version right now to see if that corrects it.  Very strange.

---

### Post by njoubert on 2008-01-28
Any word on this? I've been having a similar issue and can't get anywhere, I've tried every distribution and CD of ubuntu I could find...

---

### Post by Cynical on 2008-02-04
I'm having the same problem with Kubuntu 7.10 (x86-64). I can install the Kubuntu 8.04 (x86-64) alpha fine.

---

