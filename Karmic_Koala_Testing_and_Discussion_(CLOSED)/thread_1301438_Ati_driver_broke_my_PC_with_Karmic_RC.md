---
title: "Ati driver broke my PC with Karmic RC"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tarekeldeeb on 2009-10-26
Hello all,

I have spent 2 days  till now with no success.
I installed karmic rc x64 with the alternative CD, everything was fine. It detected the ATI hardware, I agreed to install the 'SUPPORTED' driver. I then rebooted as asked.

The boot screen with the white ubuntu logo appeared as usual, but for a couple of seconds only, then it blanked out. 
I cannot even gain access with Ctrl+Alt+F1/2/..
System is dead, I tried to remove fglrx with a rescue mode, this gives me a terminal access, but cannot fix my system !!

I even tried to 
- remove+ reinstall: fglrx, ubuntu-desktop
- dpkg-reconfigure xserver-xorg

with no success.

Can anyone help me ?

---

### Post by Mark Phelps on 2009-10-26
Have read there are troubles with ATI drivers in 9.10.

Use the link below to remove your drivers and stick with the open source drivers until this is resolved:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by tarekeldeeb on 2009-10-27
> **Mark Phelps said:**
> Have read there are troubles with ATI drivers in 9.10.

Use the link below to remove your drivers and stick with the open source drivers until this is resolved:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

thank you !

I helped greatly

---

### Post by darrenm on 2009-10-27
I'm using the open-source ati driver as fglrx does exactly the same on my Radeon HD 3400.

It has been working fine (2d only!) until today's updates where it has gone very flickery. The refresh is the same so the dotclocks must be out?

Anyone else experience this problem?

---

### Post by TrueJournals on 2009-10-27
The solution for my ATI Radeon HD 3650 was to run these two commands in recovery mode (since I couldn't do a graphical boot):
```
aticonfig --initial
aticonfig --acpi-services=off
```

You might have to play with xorg.conf a little to get aticonfig --initial to run...  (I think I had to add a "Screen" section or something... just follow the format of xorg.conf)

---

### Post by Slartius on 2009-10-29
Thanks, TrueJournals. That worked for me too on my ATI Radeon Mobility HD 3670.

For the aticonfig --initial I had to add to the "Screen" section 
of the xorg.conf file:

Device "Default Device"
Subsection "Display"
  Viewport 0 0
  Depth 24
EndSubsection

---

