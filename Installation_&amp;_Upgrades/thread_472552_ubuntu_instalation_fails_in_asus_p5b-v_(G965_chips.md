---
title: "ubuntu instalation fails in asus p5b-v (G965 chipset)"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by cuby on 2007-06-13
Hi!
I have a new asus p5b-v (latest bios) with a core 2 duo E4300, 1GB ram, a 200GB sata disk and two ide dvd-rom drives. I'm using video, sound and lan on-board.

I've tried to install ubuntu 6.06, 7.04 (32 and 64 bits) from the "normal" cds without success. In all cases the cd boots, the installation begins but halts after a while.

I've read and tried (without luck) some solutions related to the jmicron controler bug, but I don't know if this problem is related to de JMicron.

Can anyone help?... The system is bloody new and I really need it running.
Thanks.

---

### Post by cuby on 2007-06-13
Well, for everyone with the same problem ... I solved it by disconnecting one of my 2 dvd-rom drives and booting from an external usb cd-rom (dvd-rom should work) with ubuntu 7.04 on graphic safe mode. This was an extremely annoying problem. 

Lan and sound working. No 3D video acceleration... If I manage to fix it I'll say something. ;)

---

### Post by cuby on 2007-06-16
Well... the 3d drivers from intel are a pain in the ***... I just bought a cheap PCI-e graphic card.

---

### Post by Pumalite on 2007-06-16
Deleted

---

### Post by cuby on 2007-08-21
Hello!

Apparently there's another problem. 
I have two healthy PATA optical drives (asus DVD-RW and an LG CD-RW).

When I try to burn a DVD (didn't try the cd...) the operation is aborted before the end, because of a white error.

Someone knows the solution for this possible Jmicron (the pata/sata controller) error?

---

### Post by cuby on 2007-10-20
Problem solved with Gutsy Gibon. 
Jmicron's PATA stuff is working by default after the upgrade.

---

