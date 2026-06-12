---
title: "Problems installing Ubuntu on a system with IDE and SATA disks"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by ToniVC on 2006-10-13
Hi,

I'm trying to install Ubuntu 6.06.1 server on a computer where an IDE and two SATA disks are coexisting. What I want to do is to install everything on one of the two SATA disks and use the IDE disk as the /home partition. The other SATA disk is for backup purposes...

The problem is that installation goes apparently ok but then, when system boots, all I get is a black screen with a blinking cursor. No messages at all. 

When I install it on the IDE disk I have no problem at all, and the system boots OK. I think the problem must be with computer BIOS. I've defined the SATA disk as de primary boot disk, but it still doesn't work. It seems Ubuntu keeps installing the boot stuff on the IDE disk no matter the BIOS says...

Any idea? I hope you can undestand me... my English is not as good as it should :( 

Thanxs,

Toni

---

### Post by pandu.rs on 2006-10-13
I faced the same problem.. with one IDE hdd and SATA hdd.
I removed the IDE hdd while installing ubuntu as a workaround.

---

### Post by ToniVC on 2006-10-13
> **pandu.rs said:**
> I faced the same problem.. with one IDE hdd and SATA hdd.
I removed the IDE hdd while installing ubuntu as a workaround.

OK, that's what I'll do if I can't find a "cleaner" solution. Did you face any problems when connecting the IDE hdd again? :-? 

Anyway, I think it SHOULD be possible to install Ubuntu without having to remove anything! :-k 

Thanks for your answer ;)

---

