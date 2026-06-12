---
title: "Instal PowerPC Ubuntu 9.10"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by Del_Solito on 2010-05-16
Hi, I'm am trying to install Ubuntu 9.10 on my G4 Mac Mini, and I've done it before, but it crashed at an update, and I had to reinstall. The problem is that I cannot reinstall it. It will go through all the installation stuff, and then restart, but when it tries to boot it says "Please wait, loading kernel..... /pci@f4000000/ata-6@d/disk@0:3,/boot/vmlinux: No such file or directory" If anyone has any idea what is going on and could tell me how to fix this problem it would be much appreciated! (For the record, I have tried to install about 7 or 8 times over the past few days.)

---

### Post by Del_Solito on 2010-05-16
Bump

---

### Post by Wolf-Jakob Gratz on 2010-05-28
I have the same error here, although with an iMac G3 and Ubuntu 10.04.
I had 9.10 installed previously, but the dist-upgrade failed. Now I've reinstalled Ubuntu several times and can't seem to boot it once the CD installer has finished.
I suuure hope it's not a hardware fault of some kind.
So, bump.

Also, I will try installing Debian next. I'll let you know if that worked out.

---

### Post by Wolf-Jakob Gratz on 2010-05-28
Oddly enough, it finally booted. After the last failed attempt with the "No such file or directory" error, I waited a few minutes and tried it a last time before reinstalling. It booted up this thime, using the exact same kernel.

Hmm, maybe this has something to do with the HD not being ready so shortly after booting? Just a guess. I think this error has been happening before the failed dist-upgrade sometimes. This error is obviously not ideal, but as I use the iMac as a sort of home server that is permanently running, it's not that big a deal.

Del_Solito, you might try the same. Just wait a minute or so before loading the kernel at the start-up.

---

