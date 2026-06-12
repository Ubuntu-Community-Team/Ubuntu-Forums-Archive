---
title: "Install 6.06 Hang @ Booting the kernel"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by Alan87i on 2010-08-13
I'm trying to install an older version of Xubuntu 6.06 I believe. 
On a new PC Intel dual core with 4 GB of memory. 
When the (OK. Booting the Kernel ) line appears the system hangs and sits there. 
Any Ideas. 
Thanks 
Allan

---

### Post by kerry_s on 2010-08-13
why? 6.06 is long dead, repo's are gone.

---

### Post by davidmohammed on 2010-08-13
why would you want to install such an old version?

suggest play with grub boot options such as

noapic
nolapic
acpi=off
nomodeset

etc

---

### Post by linux18 on 2010-08-13
use my remastered 6.06 is fully updated: 
[http://ubuntuforums.org/showthread.php?p=9715370#post9715370](http://ubuntuforums.org/showthread.php?p=9715370#post9715370) 

and remember to use a low burn speed on the cd

---

### Post by Alan87i on 2010-08-13
It has Zoneminder installed and configured And works great with the capture cards I use. Install mod one file and go. But on this NEW PC it just locks up at booting , The live cd.

---

### Post by earthpigg on 2010-08-13
> **Alan87i said:**
> But on this NEW PC it just locks up at booting , The live cd.

no surprise. some of the key hardware on the new PC (2010), such as the cpu (i5? i7?), probably did not exist when 6.06 was released (6th month of 2006).

---

### Post by Alan87i on 2010-08-13
> **davidmohammed said:**
> why would you want to install such an old version?

suggest play with grub boot options such as

noapic
nolapic
acpi=off
nomodeset

etc

When I used the acpi=off option I actually get an error!
PnPbios: get_dev_node: invalid handle

The other options leave me at the same booting kernel hang. 
I searched through the bois and have found nothing to do with PnP.

---

### Post by Alan87i on 2010-08-13
If I use the debug option It stops at probing pci hardware (bus 00)

---

### Post by Alan87i on 2010-08-14
Anyone ?

---

### Post by snowpine on 2010-08-14
6.06 is dead. 10.04 available [here]("http://xubuntu.com").

---

### Post by jocko on 2010-08-14
> **Alan87i said:**
> Anyone ?
You've already been given the answer:
> **earthpigg said:**
> no surprise. some of the key hardware on the new PC (2010), such as the cpu (i5? i7?), probably did not exist when 6.06 was released (6th month of 2006).
On such a new pc you need an operating system with a kernel which is new enough to support your hardware.

---

### Post by earthpigg on 2010-08-14
what is it that is attracting you to 6.06? 

we may be able to find an alternative solution for you.

---

### Post by championboxes on 2010-08-14
If you are just playing around with an older version why not install it in virtualbox?

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by linux18 on 2010-08-14
> **championboxes said:**
> If you are just playing around with an older version why not install it in virtualbox?

[http://www.virtualbox.org/](http://www.virtualbox.org/)
why use virtualbox when you can chroot the old version and xnest it, it has almost no cpu and ram overhead. I'm also almost done with a script to speed up the process.

---

