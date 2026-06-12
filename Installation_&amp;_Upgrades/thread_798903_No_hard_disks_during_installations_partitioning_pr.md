---
title: "No hard disks during installations partitioning process"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by chinobar on 2008-05-18
Hi there!
This weekend i had plans of doing my 1 year old PC a favour by removing XP and install Ubuntu 8.04.
But when the installation process reaches the point of partitioning, the installer doesn't show my hard disks.

I had two attached by SATA (one via a IDE->SATA-converter), the IDE disk has been removed and the only one attached now is the SATA disk i want to install Ubuntu on.

But still, no HDs show up during the installation :/

Anyone had a smiliar problem, or know what's wrong?

---

### Post by edmccaffrey on 2008-05-18
I posted the same problem with no response:

[http://ubuntuforums.org/showthread.php?t=770756](http://ubuntuforums.org/showthread.php?t=770756)

---

### Post by chinobar on 2008-05-18
Strangely enough my motherboard also have Jmicron controllers.

---

### Post by chinobar on 2008-05-18
YAY!

I managed to make the disk appear using the extra install parameters: "*linux text _all-generic-ide pci=nommconf irqpoll_*" which i got from this thread:
[http://ubuntuforums.org/showthread.php?t=341278](http://ubuntuforums.org/showthread.php?t=341278)

Sweet god, finally a breakthrough after a long day! :P

---

### Post by chinobar on 2008-05-18
Oh well, some progress... :)

Now i keep getting a copying error: [Errno 5] input/output error
I have tried burning a new live-cd, but no luck there.

Back to searching then i guess :-P

---

