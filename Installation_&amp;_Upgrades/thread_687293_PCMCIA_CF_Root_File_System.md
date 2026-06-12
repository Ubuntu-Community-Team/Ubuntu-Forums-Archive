---
title: "PCMCIA CF Root File System"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by iceman on 2008-02-04
Hi all,
I have an old notebook with broken ide controller.
It's a Compaq Armada M700 (a realle nice notebook some years ago...)
I am trying to install Ubuntu on a PCMCIA adapter for Flash Card, booting via CDROM.
I was able to install Ubuntu on that flash card, because Ubuntu LiveCD saw it without problems.
Unfortunately, this notebook doesn't boot from PCMCIA... and i created a GRUB Boot cd.
My goal is to boot KERNEL and INITRD from cd and, after loaded right drivers, mount root fs on flash card to get system up.
Grub boot cd works perfect to boot USB (i tried and it works), but not through PCMCIA adapter.

I read almost everything in internet to solve this problem, but i didn't get it to work. I am sure i am really near the solution...
Obviously, the problem is on initrd.img.

I put yenta_socket.ko and rsrc_nonstatic.ko on /lib/modules/KERNEL/drivers/pcmcia (on initrd.img), and edited /conf/modules (always on initrd.img) and put:
yenta_socket
pcmcia_core

Saved new initrd.img, burned that on my grub boot cd and booted cd.
The boot hangs (after loading initrd.img) because it didn't see CF disk.
In busybox, i did "cat /proc/partitions" and there is nothing...
I tried modprobing some modules (pata_pcmcia), but initrd can't access CF on PCMCIA adapter.

Do you know where i am wrong?
Hope you help me... :cry:

---

### Post by iceman on 2008-02-09
An update:
i tried this grub boot cdrom on other notebooks, and it worked! Only this Compaq Armada M700 has problems with its PCMCIA Texas Instruments PCI1450.
I tried almost everything as reserve on kernel:
pci=routeirq,noacpi
reserve=42080000,0x5000
reserve=42100000,0x5000
reserve=a0000000,0x5000

Nothing... pcmcia detected, cards detected when i insert in/out, but there is no module who load partitions (i suppose it should link to sd module...). The strange thing is that Ubuntu Live CD loads pcmcia perfectly,

---

