---
title: "powernow-k8 ACPI"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Sandsound on 2009-03-29
I have wanted to try Jaunty for a long time now, but Alpha5+6 and Beta give me the same strange message :

```
Firmware bug powernow-k8 Bios does not provide ACPI PSS objects in a way that Linux understands
```

I have tried to enable Cool n quiet in my Bios (found this solution somewhere on the web), and this give me another error :

```
ph2 null fid transition 0x12
```

My specs are :

mo.bo. : ASUS M2N68
cpu : Athlon X2 5000+
ram : 4G
graphics : ATI Radeon 4830

I have no problems with Ibex or earlier version of Ubuntu

Edit: I use the i386 version.

---

### Post by Sandsound on 2009-03-29
Just a quick update.

I managed to boot it with startx, so at least I can test Jaunty now.
But still... it's a bit worrying with this error-message, so any help/suggestions will be highly appreciated.

---

### Post by cariboo on 2009-03-29
I get the same error twice. I created a bug about it and after submiitning quite a few log files and correspondence with one of the kernel devs, it comes down to a BIOS error. To correct the problem the BIOS has to be updated. If you have an MSI motherboard like me. we are s.o.l. as they haven't released any BIOS updates for my motherboard since the initial release.

Edit: BTW this error didn't show up until the 2.6.10 kernel release

Jim

---

### Post by Sandsound on 2009-03-29
> **cariboo907 said:**
> To correct the problem the BIOS has to be updated...

I am running the latest BIOS from ASUS called 0502 and still get the same message when I boot the live-cd.

Since I could start the live-cd with "startx", I went ahead and installed, and after a minor glitch with ATI and Compiz (my panels disappeared so I had to disable compiz with gnome-appearance-properties), it seams to work when I don't use visual effects.

I'm happy to hear that this have been filed as a bug already, but as I mentioned, a new BIOS did not fix the problem, so maybe the problem lies elsewhere ?

---

### Post by Rotarychainsaw on 2009-04-08
Just ran into this as well on my asus m4a79... Really wanted to try the beta too! Care to link to the bug so I can complain?

---

