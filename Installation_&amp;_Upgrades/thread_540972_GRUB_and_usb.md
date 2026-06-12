---
title: "GRUB and usb"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by Geffers on 2007-09-02
I installed Dapper Drake successfully to an external USB drive.

It did not give me any option to make a boot floppy and naturally loaded GRUB onto the external drive.

Can GRUB recognise external USB drives for manual booting?

I know GRUB counts zero as 1 etc so am aware of the differening references if I need to edit the boot location.

Geoff Lane

---

### Post by logos34 on 2007-09-04
You might find the following link useful:
[https://help.ubuntu.com/community/BootFromUSB?highlight=%28bootfromusb%29](https://help.ubuntu.com/community/BootFromUSB?highlight=%28bootfromusb%29)

---

### Post by Geffers on 2007-09-05
> **logos34 said:**
> You might find the following link useful:
[https://help.ubuntu.com/community/BootFromUSB?highlight=%28bootfromusb%29](https://help.ubuntu.com/community/BootFromUSB?highlight=%28bootfromusb%29)

I've printed this out in an effort to understand it but must confess to getting totally confused where it refers to rebuildng the initrd; it says to enter the system by entering the following;

It refers to stage2_elorito, I only have a stage2 file but in boot/grub and not usr/lib/grub as suggested in the article; would this be the same file.

Geffers

---

### Post by logos34 on 2007-09-06
> **Geffers said:**
> It refers to stage2_elorito, I only have a stage2 file but in boot/grub and not usr/lib/grub as suggested in the article; would this be the same file.

no, they're different files...On Dapper look in
[B]
/lib/grub/i386-pc[/B]

anything?

---

### Post by Geffers on 2007-09-07
> **logos34 said:**
> no, they're different files...On Dapper look in
[B]
/lib/grub/i386-pc[/B]

anything?

Thanks, copied that and all working now :)

Geffers

---

