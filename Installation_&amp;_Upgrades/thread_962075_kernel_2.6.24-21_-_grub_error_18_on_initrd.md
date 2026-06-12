---
title: "kernel 2.6.24-21 - grub error 18 on initrd"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by TheBeaNerd on 2008-10-28
I just applied a collection of system updates to a dual boot Ubuntu/XP
system (Dell Inspiron 6000) that has been working fine for some time.

Included in the updates was an upgrade to the 2.6.24-21 kernel. When I rebooted, grub failed with an error 18:

Selected cylinder exceeds maximum supported by BIOS.

Following this failure, Grub reported this error for any selection I
would make from the grub boot menu.  At this point I panicked a bit.

I was eventually able to boot XP by hand from the grub command line and
I subsequently tried to boot the linux kernel in the same manner.
However, when I performed the initrd command:

initrd		/boot/initrd.img-2.6.24-21-generic

grub failed again with error 18.

I did eventually boot my old kernel by hand and then discovered that
any of the other selections from the grub boot menu worked *as long
as I did not choose (and fail to load) the -21 image first*.

I don't know if there is something wrong with the -21 initrd image or
if it just doesn't play well with my system for some reason.  Nonetheless,
it seems bad that a failure in one boot selection would impact other
subsequent selections.

---

### Post by mmarshall on 2008-10-28
I have the same problem with kernel 2.6.24-21, but on completely different hardware.  (A recent desktop.)

Hopefully someone knows something...

MWM

---

### Post by lptr on 2008-10-29
If your previous kernel worked ok, try to modify /boot/grub/menu.lst by hand commenting out the recent kernel.

I found here in forums that some people obviously having some trouble when using a non standard partitioning schema or booting from a second, third.. harddrive or such. In previous kernel updates sometimes this caused trouble, too. 

I'm no kernel hacker. So, don't ask me for the deeper resons. Even tough - hope this will help.   

As a further hint: you could input in search line 'grub previous kernel' ... did you still trying this?

;-)

rob*

---

### Post by caljohnsmith on 2008-10-29
It could be that your BIOS has the limitation where it can't access anything on your HDD past 137 GB, as that is often the reason for a Grub error 18. Is your HDD larger than 137 GB, and does your Ubuntu partition extend past the 137 GB mark? Please post the following:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
sudo grub
grub> find /boot/grub/stage1
```
For whichever (hdX,Y) the above command returns, do:
```
grub> blocklist (hdX,Y)/boot/initrd.img-2.6.24-21-generic
grub> quit
```
And we can work from there. :)

---

### Post by mmarshall on 2008-10-29
I "fixed" the problem by changing my sata from "AHCI" to "Native IDE"  (Or something like that.)  As I understand it, this prevents me from hot-plugging SATA drives, but that's not a big deal at the moment.

Yes, my hard drive is larger than 137GB, and recently I've filled up more than 200GB of it while editing video.  So that must be the problem.  Eventually I'll chop it up with separate partitions for OS and data.

MWM

---

