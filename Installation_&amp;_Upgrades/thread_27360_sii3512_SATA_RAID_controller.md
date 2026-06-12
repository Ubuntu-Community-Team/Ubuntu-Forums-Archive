---
title: "sii3512 SATA RAID controller"
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by mun3kh on 2005-04-15
Silicon Image make this SATA RAID controller, and I have one on my:
Gigabyte GA-7N400 Pro2 - Motherboard

I have two 120Gb Maxtor SATA Drives in a Mirrored Set (RAID 1?)
Onto this are two NTFS partitions, one has WindowsXP on, the other simply data (work, music etc.)
I have deliberatly left space on this Mirrored set, about 30Gb for Ubuntu 5.04 (Hoary)

I burned a new iso of Hoary to CD and went to install Ubuntu, sadly it
detects my two drives separately. 
If I try and install it onto one of them, it will ruin the idea of having a Mirrored set ](*,) 

So my problem is, how do I get the Hoary installer to detect my Mirrored
set as one drive?


It is my understanding that this particular RAID controller may not be
strictly hardware RAID, and this is why the Hoary installer can see the
two drives separately.
Here is a page of drivers for this controller: [http://www.siliconimage.com/support/downloadresults.aspx?pid=29&bios=0&drivers=0&sataraid=0&](http://www.siliconimage.com/support/downloadresults.aspx?pid=29&bios=0&drivers=0&sataraid=0&)

I have no idea how to incorporate drivers into an installation, or if any of these drivers will work with Hoary

---

### Post by eventures on 2005-07-01
I have a Silicon Image SiI3114. 

I'm experiencing the same problem as well. the installer sees my drives as seperate drives....

anyone out there can help??

---

### Post by norman_h on 2005-07-05
[QUOTE=mun3kh]It is my understanding that this particular RAID controller may not be
strictly hardware RAID, and this is why the Hoary installer can see the
two drives separately.
[/QUOTE]

Thats the problem!  I have had the same problem.  I'd love to setup RAID0, but it aint gonna happen easily.  I managed to find some info on mailing lists sometime ago and I concluded that it would be possible to do it, however, since I had no need for RAID1 I didn't make notes about it.  I found that with a lot of hacking it is also possible to get RAID0 working partially in a very hacked sort of way.

I have a GA-K8NS-ultra-939 mobo with the Sil3112 chipset.

The method involved something like putting the raid modules in the initrd image so that the kernel would be able to have access to the RAID partitions at boot time.  There would also have to be a seperate /boot partition that was on a non-RAID partition where the initrd image would reside.

If you want to get ubuntu to use a seperate partition as a RAID partition (for storage)  then create two identical partitions of type linux raid autodetect, use the mdadm tool to create the RAID partition on these two drives, format it, mount it and away you go!

---

