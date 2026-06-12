---
title: "Unable to boot at all"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by meznaric on 2007-08-25
Hi guys. I installed GRUB and Ubuntu on an old laptop via the network install. The laptop also has WinXP. After booting Ubuntu froze immediately so I decided to do fsck on the partition. Now that seems to have rendered the partition unusable and therefore GRUB can no longer access its files on the partition and therefore the laptop is unable to boot (Grub reports error 17 at stage 1.5). The problem is the laptop can boot from nothing other than the hard drive. Is there a way to configure GRUB to boot without accessing any files? Any other ideas would be appreciated too.

---

### Post by Daveth on 2007-08-25
the easiest way for you to do this as you do not seem to have a live cd to hand would be to download a copy of Supergrub. See

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

for details. If you set the laptop bios to boot from the cd drive, when you turn on the power, pop supergrub into the cd drive and it will boot itself up. Then just move through the options till to get to the repair boot section- I cannot remember the detail here but it is obvious. Error 17 seems to be a grub favourite; there are plenty of posts about repairing grub.

---

### Post by meznaric on 2007-08-26
That's the problem. It is not possible to boot from a CD for some reason. When selecting the CD option from the boot menu it is simply ignored and the computer boots from the hard drive. In effect it is not possible to boot from anything other than the hard drive (USB boot is not supported and the laptop does not have a floppy drive). 

I think the only option would be to somehow edit the GRUB boot options manually from GRUB itself. Is there a button one could press to get GRUB to display the editor for the boot files?

---

### Post by Daveth on 2007-08-27
the only way I know is either to load up a live linux cd, and edit the grub files from there, or let Supergrub do it for you. 
If you installed ubuntu by a network download how do you know it will not boot from either a live cd or a Supergrub disk? Have you tried a live cd? Bear in mind it is not a copy of a live disk but an iso file. You will not lose anything by making a Supergrub cd, as it is a very handy utility.

If you have tried these then you might explore hardware options, such as putting a new cd drive in- without this your laptop is pretty hobbled anyway ansd again you will not lose anything by doing it.

---

### Post by Pumalite on 2007-08-27
Try updating your BIOS. Maybe that's your problem; unless the CD drive is broken or badly connected.

---

### Post by meznaric on 2007-08-27
No CD boots at all. I tried Windows CD and Ubuntu Live CD. This has been a problem for awhile. Changing the CD drive might work who knows.

As for the BIOS, yes I agree it could be a problem with BIOS. But without being able to boot the computer I cannot upgrade the BIOS.

---

### Post by Pumalite on 2007-08-27
You might want to try this:

[http://www.google.com/products?q=USB+floppy+for+laptops&hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=FN9&um=1&sa=X&oi=froogle&ct=title](http://www.google.com/products?q=USB+floppy+for+laptops&hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=FN9&um=1&sa=X&oi=froogle&ct=title)

Besides flashing your BIOS, you could do a net install.

---

### Post by meznaric on 2007-08-28
I have tried booting with the USB key. That does not work ... The computer does not support booting from USB. There goes the USB floppy idea as well ...

---

### Post by Pumalite on 2007-08-28
It looks like if you have a working computer, you have to change your CD drive.

---

