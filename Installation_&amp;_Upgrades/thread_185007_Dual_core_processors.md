---
title: "Dual core processors?"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by adwait on 2006-05-30
Hello!

Do dual core processors fall under the description of x86 processors? ie: Can I use the x86 version of Ubuntu for a system using the Intel Pentium D? Also, how much of a difference can i expect between a P4 and a Pentium D?

Adwait

---

### Post by DarthMandeep on 2006-05-30
Dual core processors from AMD and Intel are x86 based, so you can use the x86 version of Ubuntu on them.

As for the difference between a Pentium 4 and Pentium D, the D might be faster in general use, but you'll notice the difference mostly when running multiple proc-intensive apps. That's where I see the most improvement with my Athlon X2.

---

### Post by Arnaud_B on 2006-05-30
I would just add that pentium D supports emt64 I think so you could install the 64 bits version of ubuntu...
A.

---

### Post by garretwp on 2006-05-30
Also when you have a dual core chip like the AMD x2 or Pentium D and the new Core 2 Duo that have the 64bit extension, you can run the 32bit x86 version or the 64bit x86 version of the Ubuntu distros. But be aware that the 64bit version still have software compatiblility issues.

Garrett

---

### Post by slavik on 2006-05-30
[QUOTE=Arnaud_B]I would just add that pentium D supports emt64 I think so you could install the 64 bits version of ubuntu...
A.[/QUOTE]
no. EMT64 is not x86-64 (AMD and 64bit Ubuntu)

IA32 (Intel Architecture 32) = x86 (32bit)
IA64 (Intel Architecture 64) = EMT64, I believe P4/D emulate x86-64 and some even do it natively, or not at all ... one of the 3.

---

### Post by Arnaud_B on 2006-05-30
[QUOTE=slavik]no. EMT64 is not x86-64 (AMD and 64bit Ubuntu)

IA32 (Intel Architecture 32) = x86 (32bit)
IA64 (Intel Architecture 64) = EMT64, I believe P4/D emulate x86-64 and some even do it natively, or not at all ... one of the 3.[/QUOTE]

Nope, emt64 *is* x86-64 or amd64 whatever we call it and IA64 is Itanium which is very different. I'm using a pentium emt64 with the amd64 version of ubuntu.
A.

---

### Post by garretwp on 2006-05-30
EMT64 is the same as AMD64. Just a different way of doing it. They are both compatible with eachother. 

Garrett

---

### Post by dyndyn on 2006-07-19
hi. im new to ubuntu. im running ubuntu dapper on older pcs and our celeron d pc's. the live cd works fine. but when i run it on an intel 805 2.66 dual core 533 mhz, i get the boot screen to run and install. But when i click install, it hangs up after the kernel are loaded. what could be the problem. hope you can answer my question. thanks!

---

### Post by bsalt on 2007-01-25
I just installed Ubuntu Edgy x86-64, and I am encountering numerous bugs with it. Do you guys know if Dapper x86-64 is better for 64 bit?

---

### Post by housam on 2007-01-25
> **bsalt said:**
> I just installed Ubuntu Edgy x86-64, and I am encountering numerous bugs with it. Do you guys know if Dapper x86-64 is better for 64 bit?
Dapper with less features than Edgy is more stable with less bugs.

---

