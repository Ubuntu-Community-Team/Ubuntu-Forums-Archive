---
title: "Install not working on Dell Inspiron (desktop)"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by lookinggood123 on 2008-04-28
Hi,

I have tried to do a fresh install of uBuntu 8.04.

When I boot from the CD and select any of the menu options the system just gives me the following prompt (it loads for a minute and then gives me the prompt):

"
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12)Built in shell (ash)
Enter 'help' for a list of built in commands

(initramfs)_
"

Why does the ubuntu installer not load? Why is it going to a bash shell prompt?

I have done a checksum on the CD and its fine?

Any one having similar problems?

---

### Post by Pumalite on 2008-04-28
Try the Alternate CD to avoid possible hardware and/or graphics problems. It's text based and much easier to use. Gives more control too.

---

### Post by Plath on 2008-04-28
I have exactly the same problem and the same computer (inspiron 530). I tryed all methodes of installation (alternate CD, live CD, upgrade from 7.10) and i have the same error than lookinggood123 when i boot on 8.04. After (initramfs)_ I have this [http://paste.ubuntu-nl.org/64669/](http://paste.ubuntu-nl.org/64669/) .

  I hope this problem will be fixed (does inspiron 530n desktop with preinstalled ubuntu 7.10 have the same problem than my inspiron 530 ?).

---

### Post by lookinggood123 on 2008-04-28
Does anyone know how to solve this problem?

This is a very common Dell Machine (530) and you cannot get ubuntu 8.04 installed on it. Surely ubuntu would have tested the OS on common Dell machines (dell being the only major computer manufacturer to ship ubuntu to home users).

---

### Post by Plath on 2008-04-28
Lookinggood123, this tread is about the problem we have : [http://ubuntuforums.org/showthread.php?t=719483](http://ubuntuforums.org/showthread.php?t=719483)

---

### Post by lookinggood123 on 2008-04-28
Thank you

---

### Post by Plath on 2008-04-28
I successfuly booted on 8.04 with my inspiron530 just by changig SATA from IDE to RAID (in the bios) as explained in :
 [http://ubuntuforums.org/showthread.php?t=719483](http://ubuntuforums.org/showthread.php?t=719483)

  So my problem is fixed.

---

### Post by mikemunsil on 2008-11-20
> **Plath said:**
> I have exactly the same problem and the same computer (inspiron 530). I tryed all methodes of installation (alternate CD, live CD, upgrade from 7.10) and i have the same error than lookinggood123 when i boot on 8.04. After (initramfs)_ I have this [http://paste.ubuntu-nl.org/64669/](http://paste.ubuntu-nl.org/64669/) .

  I hope this problem will be fixed (does inspiron 530n desktop with preinstalled ubuntu 7.10 have the same problem than my inspiron 530 ?).

Yes, it does.

---

