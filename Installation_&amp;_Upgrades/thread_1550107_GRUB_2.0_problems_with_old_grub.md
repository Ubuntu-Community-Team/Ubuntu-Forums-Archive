---
title: "GRUB 2.0 problems with old grub"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by ElevenWarrior on 2010-08-10
okay, so here's my problem

I have installed, Ubuntu 10.4, Windows 7, and backtrack 4.
I have to install them in this order (windows, backtrack, then ubuntu) otherwise it woln't work.
well backtrack released a new distro so I have to reinstall it.
if I do, what happens is backtrack 4 grub overwrites the 10.4 grub, but the backtrack grub (1.95 I think) will NOT boot into ubuntu.

So basically, I need to know how to (after reinstalling backtrack 4) to tell the machine to use the ubuntu grub, (2.0) instead of the backtrack grub. (older verison)
Any ideas?

---

### Post by drs305 on 2010-08-10
If you want Ubuntu's Grub2 to control things, reinstall Grub2 from the Ubuntu Live CD:

```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX

```

For example, if your Ubuntu install is on sda5, the commands would be:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

This will install Ubuntu's grub on the MBR of the device you designate (example: sda) and write the grub files to the Ubuntu partition (example sda5).

Grub2 should recognize your other OS's. If it doesn't, run "sudo update-grub" after booting into your normal Ubuntu OS.

---

### Post by ElevenWarrior on 2010-08-12
I tried doing those steps you said, but it didn't work.
I installed grub to the right part of the drive, but at next start up, the old grub was still there.
It did, however, say I was installing the GRUB to only that partition and not the MBR, which it said was  a bad idea.
still stuck,

---

### Post by oldfred on 2010-08-12
You installed to the partition not the drive. Drives are sda, sdb etc. Partitions are sda1, sda2, sdb1 etc.

Redo drs305's instructions but the last entry does not have a number.

sudo mount /dev/sda5 /mnt   [COLOR=Red]<--- number has to be your Ubuntu partition.[/COLOR]
sudo grub-install --root-directory=/mnt /dev/sda   [COLOR=Red]<--no number at end[/COLOR]

---

