---
title: "Instalation of 9.04 beta doesn't work :("
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by schnelle on 2009-04-13
Versions 8.04 and 8.10 worked normal but when I try to install Jaunty I get this message:

"[some number] ata1: softreset failed (device not ready) modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep

Busybox...."

I have MSI EX610 laptop, ATI mobility radeon hd 2400, 160GB HDD, 2GB RAM.

I tried the same installation of Jaunty on my roommate's laptop and it works.

Please help. Thanks.

---

### Post by schnelle on 2009-04-13
I have to wait final release and hope it will work, right? 

No help for me. :(

---

### Post by crysys on 2009-04-17
I've been fighting the same problem on an Acer Extensa 4420 with AMD 64 X2 cpu and ATI Xpress 1250.

This bug got me past the error:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350946]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350946")

Daniels solution is scary and hacky but it works.  Pull the usb stick out shortly after the ubuntu load screen pops up, and then plug it right back in again.  There is some kind of serious hardware glitch causing this but reinserting the usb stick seems to bypass it.

If your booting from a cd I don't know if it will work.

---

### Post by schnelle on 2009-04-18
> **crysys said:**
> I've been fighting the same problem on an Acer Extensa 4420 with AMD 64 X2 cpu and ATI Xpress 1250.

This bug got me past the error:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350946]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350946")

Daniels solution is scary and hacky but it works.  Pull the usb stick out shortly after the ubuntu load screen pops up, and then plug it right back in again.  There is some kind of serious hardware glitch causing this but reinserting the usb stick seems to bypass it.

If your booting from a cd I don't know if it will work.

Thanks. I'll give it a try :)

P.S. 9.04 rc doesn't work as well as beta version

---

### Post by schnelle on 2009-04-18
> **crysys said:**
> I've been fighting the same problem on an Acer Extensa 4420 with AMD 64 X2 cpu and ATI Xpress 1250...

Thank you a lot for the reply but it doesn't work for me. I tried many times but no luck for me :(

I hope they will fix the bug in final release.

Thanks again.

---

### Post by olskar on 2009-04-18
Try releasecandidate instead of beta :)

---

### Post by schnelle on 2009-04-19
> **olskar said:**
> Try releasecandidate instead of beta :)

I have tried, but I get the same error :(

---

### Post by schnelle on 2009-04-19
I gave up trying to boot from usb flash drive.

From CD it shows the same error but i can log in in live session and i can run installation.

---

### Post by markbuntu on 2009-04-19
I have been getting those messages since alpha4 but Jaunty boots up anyway for me...

---

