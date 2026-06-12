---
title: "Samsung Ativ 9 Plus - Safe to install Ubuntu?"
date: 2013-10-09
forum: Installation &amp; Upgrades
---

### Post by oh my on 2013-10-09
Hi Guys,

I recently bought a Samsung Ativ 9 Plus (940x3g) and would like to  install (k)ubuntu on it. However, there is the issue of the BIOS bug  with Samsung that bothers me. I haven't been able to find any  information whether this was fixed from Samsung's side or not.

So I was wondering if anybody has any experience installing Ubuntu as a  Dualboot to Win8 on the Ativ 9 Plus and if there are things that need to  be taken into account? Can I install Ubuntu safely with UEFI? Is it  possible to dualboot win8 & ubuntu on it?  Is it better to install  13.10 straight away or should I install 13.04 now. Can 13.04 (13.10)  handle haswell?

regards
oh my

---

### Post by oh my on 2013-10-11
*bump*

---

### Post by oh my on 2013-10-14
Hi,

I've since contacted Samsung Customer Support. They said that the Series 9 was never affected by the UEFi bug and that in any case a BIOS update had been pushed out already to address the issue on affected machines.
I've only tried running a live-cd for now, but that has worked well except for some minor issues with resolution and such.

You can consider this resolved.

---

### Post by Steven_Thibault on 2013-10-15
What did you have to change to boot from a live CD, and did you use a thumb drive, or an SD card?

---

### Post by oh my on 2013-10-15
Hi,

I disabled fastbios and  then secureboot. Once you've done that under secureboot you get a menu called OS Mode selection. I selected CSM OS and saved the settings. Then I could boot from the Live-CD. 

If you want to boot into win8 again, you need to first set the OS Mode Selection back to UEFi, then reenable secure boot and fastbios.

regards
oh my

---

### Post by jfburkhart on 2013-11-20
Just wanted to confirm that this worked for me as well, running off a USB live CD. What a nice machine! Just wish it came with more hdd space!

---

### Post by amitk2 on 2013-12-19
> **oh my said:**
> Hi,

I disabled fastbios and  then secureboot. Once you've done that under secureboot you get a menu called OS Mode selection. I selected CSM OS and saved the settings. Then I could boot from the Live-CD. 

If you want to boot into win8 again, you need to first set the OS Mode Selection back to UEFi, then reenable secure boot and fastbios.

regards
oh my

Did you have to do anything special to get Ubuntu to *boot* after the installation in this method?

The problem is that by selecting CSM, Ubuntu (and thereby, grub) is installed Legacy BIOS mode. It would be nice if we could just install it in UEFI mode so this toggling in the BIOS wouldn't be needed.

---

### Post by akukuq on 2014-01-22
*bump*

---

