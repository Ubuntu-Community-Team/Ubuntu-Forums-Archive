---
title: "How to effectively prevent kernel updates?"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by jogeba on 2010-07-15
Hi,

I have a bunch of machines (running 10.04) that should be periodically updated using 'apt-get upgrade' but I don't want kernel updates because the machines must run without interruption.

I know I can hold a package with 'echo <paketname> "hold" | dpkg --set-selections' but I don't know what packages to hold.

Can I just hold 'linux-generic-pae' or do I need to hold explicitely e.g. 'linux-image-2.6.32-22-generic-pae'?

What other packages do I need to hold?

Greetings

Josef

---

### Post by andrewthomas on 2010-07-15
> **jogeba said:**
> 


Can I just hold 'linux-generic-pae' or do I need to hold explicitely e.g. 'linux-image-2.6.32-22-generic-pae'?

What other packages do I need to hold?

Greetings

Josef
linux-image-2.6.32-22-generic-pae.  If you hold the specific image, you will prevent all kernel updates.

---

