---
title: "No disk drive detected AMD 64"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by Paladiamors on 2008-07-08
System specs:

AMD 5200+ x2 Athlon CPU
4 GB ram
2x Seagate 500 GB SATA HD (ST3500320AS)
GF8200A Black ECS Mobo
GeForce9600GT Video card 512 MB

Installing with the AMD64 bit operating system CD, alternative version 8.04

Can't seem to detect the HDs with ubuntu. Tried the HDs in AHCI, SATA and RAID but to no avail.

The HDs are brandnew and unformatted.

Any help would be greatly appreciated.

Thanks in advance.

---

### Post by Afkpuz on 2008-07-08
Are the drives detected in bios?

---

### Post by Paladiamors on 2008-07-08
yep the hard drives are certainly there :)

---

### Post by Pumalite on 2008-07-08
Format your drives and try again. Ubuntu cannot be installed in unallocated space.

---

### Post by Master Chief on 2008-07-08
I had to disable the on-board IDE controller (unused for SATA drives) and all went smooth from there on.

---

### Post by Paladiamors on 2008-07-08
Thanks for the replies so far.

I think I should add some extra details about the problem. The BIOS finds the HDs and during installation, the installer does not find the HDs during the detection phase of the installation.

I am asked to select a driver for my hard disks but going through the list I cannot find anything that will find my hard drives. As the hard drives cannot be found, I cannot make partitions do any formatting. 

Is it OK to disable IDE support? I have to use my CD-rom to install Ubuntu.

Thanks~

---

### Post by Master Chief on 2008-07-08
> **Paladiamors said:**
> Thanks for the replies so far.
Is it OK to disable IDE support? I have to use my CD-rom to install Ubuntu.
Thanks~

Oh blimey :(  Man that is a good one! Sorry for that.  

[COLOR="Red"]Ouch! Your motherboard is not supported with a pre-2.6.25 Linux kernel (the Serial ATA won't work).[/COLOR]

---

### Post by Paladiamors on 2008-07-09
Thanks for the heads up Chief. Do you think it would be possible to install to an IDE drive, upgrade to the 2.6.25 kernel and then migrate the system over to my SATA drives? Or does it mean that my SATA is not supported including on the 2.6.25 kernel?

Thanks for finding out that info.

---

### Post by Master Chief on 2008-07-09
> **Paladiamors said:**
> Thanks for the heads up Chief. Do you think it would be possible to install to an IDE drive, upgrade to the 2.6.25 kernel and then migrate the system over to my SATA drives? Or does it mean that my SATA is not supported including on the 2.6.25 kernel?

Thanks for finding out that info.

It means that you'll have to compile your own kernel, which includes the missing drivers for your motherboard.  You should first do a Google search for the drivers for you motherboard.

I'm pretty sure that the next link will help you:

[http://cdimage.ubuntu.com/releases/intrepid/alpha-1/](http://cdimage.ubuntu.com/releases/intrepid/alpha-1/)

It's only an Alpha, but check if that installs.

---

