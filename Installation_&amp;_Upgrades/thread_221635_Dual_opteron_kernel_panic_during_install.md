---
title: "Dual opteron kernel panic during install"
date: 2006-07-23
forum: Installation &amp; Upgrades
---

### Post by jshevland on 2006-07-23
Hi

I'm trying to install Ubuntu 6.06 on a dual opteron server and I get a kernel panic as soon as selecting the Install option - I've tried both CD's so the text mode install as well as the normal one. Here's the message straight after pressing enter to start the install off:

PANIC: early exception rip ffffffff8046c58d error 0 cr2 3440
PANIC: early exception rip ffffffff8011e35a error 0 cr2 ffffffffff5fd023

The "Loading Linux Kernel" dialog appears before that and progresses up to 100%, albeit with one or two line of screen corruption, then the panic.

The machine is a dual opteron with 2GB ram, 4 SATA disks on an Sii software raid controller, K8SD Pro Tyan motherboard.

I've tried the various suggestions I've been able to google, including acpi=off, noapic, nolapic etc but the most I've been able to do is change the panic message with those.

Any other ideas before the CD's become coasters?

---

### Post by jshevland on 2006-07-24
Coasters it is. If an admin happens to see this post, feel free to delete this account, I couldn't see a method in the user CP.

---

