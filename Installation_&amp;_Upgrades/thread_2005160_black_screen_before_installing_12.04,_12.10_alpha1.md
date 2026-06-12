---
title: "black screen before installing 12.04, 12.10 alpha1"
date: 2012-06-17
forum: Installation &amp; Upgrades
---

### Post by aaronp on 2012-06-17
Hi all,
I'm trying to install Quantal Alpha 1 i386 in VirtualBox (4.0.4_OSE r70112) but running into a problem every time. I've actually tried it with both Qantal Alpha 1 Desktop and Alternate ISOs, Quantal daily build Desktop ISO as well as the 12.04 official release ISO, all with the same result.

First I had to turn on PAE in the VM. No problems, now allows me to get to the try/install screen...

Upon reaching the try/install screen if I choose either of those options I go immediately to a black screen with a single white (underscore-shape) cursor and it immediately hangs my entire system (not just the VM, my host system too - requiring a hard reset).

I have read that it may be a case of adding 'nomodeset' to the boot options but strangely I cannot press F6 at that screen before proceeding to install/try. I can press all keys F1 to F5 as normal but F6 does not work at all. (I've tested F6 separately and it is working fine)

My host system is Ubuntu 11.04. I've attached my latest VM log in case it's helpful.

thanks
Aaron

---

### Post by aaronp on 2012-06-23
Bump...Anyone? thanks

---

### Post by aaronp on 2012-06-30
bump again...

---

