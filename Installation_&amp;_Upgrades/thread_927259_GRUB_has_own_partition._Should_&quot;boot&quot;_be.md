---
title: "GRUB has own partition. Should &quot;/boot&quot; be mounted there ?"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by brjoon1021 on 2008-09-22
Hi,
 
I am installing Ubuntu Ultimate Edition, which is a variant of Ubuntu with lots of candy added. Anyway, I want to have my "/" and '/home" partitions as XFS. XFS will not hold GRUB without a bunch of trouble that I want to avoid.
 
I created a small ext3 750 MB partition at the front of the hard disk for GRUB to be happy in. Ubuntu UE will be on hda3, Windows on hda2. As I am installing Ubuntu, do I put the "/boot" partion on that ext 3 that I made for GRUB ?

---

### Post by caljohnsmith on 2008-09-22
> **brjoon1021 said:**
> Hi,
 
I am installing Ubuntu Ultimate Edition, which is a variant of Ubuntu with lots of candy added. Anyway, I want to have my "/" and '/home" partitions as XFS. XFS will not hold GRUB without a bunch of trouble that I want to avoid.
 
I created a small ext3 750 MB partition at the front of the hard disk for GRUB to be happy in. Ubuntu UE will be on hda3, Windows on hda2. As I am installing Ubuntu, do I put the "/boot" partion on that ext 3 that I made for GRUB ?
Yes, I believe that is all you need to do; set your 750 MB partition mount point to /boot during the installation and you should be all set.

---

### Post by brjoon1021 on 2008-09-23
thanks, but the GRUB installation did not work for some reason...

---

### Post by caljohnsmith on 2008-09-23
> **brjoon1021 said:**
> thanks, but the GRUB installation did not work for some reason...
Can you be more specific? What exactly happened? And how is Grub not working? Any Grub errors? What happens on start up?

---

