---
title: "Newest kernel cant detect disks"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by ingeva on 2010-08-08
I'm running Ubuntu 9.10 Karmic Koala, and the latest kernel upgrade (xxxx.22) won't start the system because it can't find the hard disks. It ends up with a prompt from (initramfs).

The computer has an MSI board with Intel P4 Dual CPU, and a Phoenix Award BIOS marked W7037 IMS V1.2, dated 091604 (Sep16/04).
I doubt that a newer BIOS that will fix the problem, but if anyone knows I could try to find a floppy drive and a diskette, because they require that to install the newer BIOS (ver 1.3). Does any one have a better method?

Anyway, could there be a better solution to the problem? Is it still possible to get the previous kernel version until they fix this bug (if they ever will)?

Is there a way to change the boot sequence in GRUB2 so the original kernel would be the default even if the rest of the software has been updated?

Since 10.04 has several bugs and annoyances, may be it's time to change to another distribution (I've tried Mint 9, but it has much of the same, like having to enter the password if I take a short break from the computer).

Many questions at once, but less and less things are functioning with each new revision.
For instance to use the scanner I must go back to 8.04, or use WINDOWS! (The scanner is the only reason why I have Windows on the computer) :(

---

### Post by dino99 on 2010-08-08
at end of bios process, hold "shift" key down to see thr grub menu; from there select the original kernel to boot, then into synaptic, update the sources and remove/purge the broken kernel (each related package: header, image, lbm if any) then reinstall it

if you want to always see the grub menu, edit the config file:

sudo gedit /etc/default/grub

and change " grub_hidden_timeout_quiet" to false,
 then
 sudo update-grub

startup-manager can tweak the grub menu order if installed

---

### Post by ingeva on 2010-08-08
> **dino99 said:**
> at end of bios process, hold "shift" key down to see thr grub menu; from there select the original kernel to boot, then into synaptic, update the sources and remove/purge the broken kernel (each related package: header, image, lbm if any) then reinstall itOK, no problem with seeing the grub menu, but since this computer is supposed to boot without my being there I would need two things:

1. Ability to edit the grub menu  (Never found instructions for GRUB2!)
2. Install the previous kernel: What files do I need, kernels and all header files?

---

