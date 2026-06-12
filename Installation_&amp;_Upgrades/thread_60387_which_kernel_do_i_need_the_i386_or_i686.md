---
title: "which kernel do i need the i386 or i686"
date: 2005-08-27
forum: Installation &amp; Upgrades
---

### Post by doronunu on 2005-08-27
im using the 2.6.10-5-386 kernel

 or but ineed compile it to smp and i want to now if i need to comile it to i586
or i686 how can i know?

my processor is intel pentuim 4 2.8 HT.

---

### Post by bored2k on 2005-08-27
[QUOTE=doronunu]im using the 2.6.10-5-386 kernel

 or but ineed compile it to smp and i want to now if i need to comile it to i586
or i686 how can i know?

my processor is intel pentuim 4 2.8 HT.[/QUOTE]
 From a terminal:
sudo apt-get install linux686-smp

---

### Post by evilghost on 2005-08-27
You want 686-smp.

Run this command in terminal, then reboot.

```

sudo apt-get install linux-686-smp

```

---

### Post by doronunu on 2005-08-27
do i need to change something in my lilo?

---

