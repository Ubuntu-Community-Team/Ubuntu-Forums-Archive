---
title: "Error: No symbol table found - after upgrade from Ubuntu 16.04 to 16.10 (64 bit)"
date: 2016-10-17
forum: Installation &amp; Upgrades
---

### Post by mirmos192 on 2016-10-17
After upgrading-in-place (yes, I know, but it's so much more *convenient*...) from Ubuntu 16.04 to 16.10, the error 'no symbol table found, press any key to continue' comes up. 
If you don't press 'any key' the login screen eventually appears anyway and all appears well. If you do press 'any key' it just brings the message up again. I note that a bug has been reported [lpbug]1633839[/lpbug], but I cannot find a lot of other reports with the same error (there are a few) but no fixes or satisfactory workarounds yet.
This is, needless to say, very irritating because apart from being untidy it seems to be slowing down my starting Ubuntu 16.10.
Does anyone have any bright ideas?
Best
David

---

### Post by jalefkowit on 2016-10-17
I'm experiencing the same thing. I also did an in-place update from 16.04 to 16.10.

---

### Post by mirmos192 on 2016-10-19
Since last posting I have tried 'boot-repair' in normal and advanced mode and have tried reinstalling grub via sudo grub-install /dev/sda1 (then sda2, and finally simply sda). All of these approaches have reported 'success' in bash/terminal etc - but none have actually solved my problem. However, two other people, elsewhere, have reported success by reinstalling grub by one of these methods (see Michka and Alex N here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1633839](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1633839) ). 
Actually I'm wondering where my 'working' grub is actually installed. I have a UEFI machine which originally came with Windows 8. On installing Ubuntu I did what was necessary to allow Ubuntu 14.04 to be installed successfully instead of Windows, and have 3 partitions: sda1 is allegedly my boot partition (Fat 32), sda2 my main partition and finally there is a sda3 - for Linux-Swap. I suppose it is possible I have two grubs installed, one in sda1 and the other in sda2. Is it possible that a delay in reaching the 'working' grub (say in sda2) is provoking the 'no symbol table found' error in Ubuntu 16.10?

---

### Post by habana on 2016-11-22
After upgrading from 16.04 to 16.10 I have the same bug and have added my click to the "affects me too" button on the launchpad bug link.

---

### Post by dkrix on 2016-12-30
Affects me as well. I'm sure I've seen that button before, but can't see it anywhere this time around.

---

### Post by dkrix on 2016-12-30
Apologies, didn't read "in launchpad".

---

### Post by dmoss on 2017-05-07
I've got the same symptom with fresh install (formating UbuntuStudio 15.10 on / to 17.04, same /home).

---

### Post by oldos2er on 2017-05-07
Please start a new thread for your problem.

---

