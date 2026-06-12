---
title: "Edgy didnt install with SMP ?? Help me upgrade kernel"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by m1 grant on 2007-01-15
I recently made a 6.10 installation and I was under the impression that by default the kernel should detect and support smp processors, mine is a amd X2 and i used the 32-bit version of ubuntu because I wanted more software compatability. My system monitor only shows one core, and I can tell that the computer slows down way more than a dual core system should. Also my "uname -a" spits this out > Linux mustang 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686 GNU/Linux
  and says nothing about SMP. Could someone tell me the easiest and painless way to upgrade the kernel without disrupting to many packages and devices.:confused:

---

### Post by Enverex on 2007-01-15
You need to select the "Generic" one rather than the "i386" one in Synaptic (it's litterally named "linux-generic").

---

### Post by m1 grant on 2007-01-15
will this cleanly upgrade my kernel or will several devices and packages need to be updated manually by doing this (ie Im running Myth, nvidia driver, and ivtv, which have been known to not like these sort of things)

---

### Post by m1 grant on 2007-01-15
also when i look it up in synaptic it says its already installed. so why isnt it working?

---

### Post by Enverex on 2007-01-15
You need to change your /boot/grub/menu.lst file to boot the Generic one then.

---

### Post by m1 grant on 2007-01-15
sorry, not that good at linux yet, could you tell me what line I am looking for and how I should edit it?

---

### Post by m1 grant on 2007-01-15
I figured it out, for any1 with the same problem. You just change the /boot/grub/menu.lst (like he said), but more specifically change all instances of "386" into "generic"

---

