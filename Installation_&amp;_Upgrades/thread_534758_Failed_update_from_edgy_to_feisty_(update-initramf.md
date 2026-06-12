---
title: "Failed update from edgy to feisty (update-initramfs)"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by christhemonkey on 2007-08-25
**Summary**
[INDENT]update-initramfs fails to work *causing dist-upgrade to fail!*[/INDENT]


**Background**
[INDENT]My brother asked me to install the libdvdcss2 library so he could watch dvd's on his laptop running edgy eft whilst in Germany (he is going there for a year, leaving tomorrow)
Being the helpful brother I am, I said I would upgrade him to feisty whilst I was doing that.[/INDENT]


**The problem**
[INDENT]After downloading all needed packages, the laptop then proceeded to just sit there on the configuration of a certain package (dmsetup), it sits there saying:
```
update-initramfs: Generating /boot/initrd.img-2.6.17-10-386 
```
[/INDENT]

**What I have tried**
[INDENT]After a (long) while I gave up waiting for the initramfs to be regenerated, I have tried reconfiguring that just package, but that also fails on the same problem.
I have tried just running a 
```
sudo update-initramfs -u -k 2.6.17-10-386 
```
and a
```
sudo mkinitramfs -o /boot/initrd.img-2.6.17-10-386
```
but this also just hangs I have also tried reinstalling initramfs-tools. These seem to be the only solutions I could find from extensive google-ing.[/INDENT]


Any help is very very much appreciated (before my brother actually kills me!)

---

### Post by christhemonkey on 2007-08-25
Ok problem solved, all it needed was, booting from an older kernel with a working initrd (as i had deleted the one for the running kernel) then having a little patience.

Bit of a relief.

---

