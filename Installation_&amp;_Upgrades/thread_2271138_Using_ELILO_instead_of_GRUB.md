---
title: "Using ELILO instead of GRUB"
date: 2015-03-27
forum: Installation &amp; Upgrades
---

### Post by checoimg on 2015-03-27
How do I make Ubuntu use ELILO or LILO instead of GRUB ?

 Thank you

---

### Post by LinuxAlexs on 2015-03-27
Why? It's dead Jim...

[http://sourceforge.net/projects/elilo/](http://sourceforge.net/projects/elilo/)

---

### Post by checoimg on 2015-03-27
oooh... Do you know any option for using EFI with Ubuntu ?, 32 bit processor.

---

### Post by Vladlenin5000 on 2015-03-27
> **checoimg said:**
> oooh... Do you know any option for using EFI with Ubuntu ?, 32 bit processor.

There's no 32-bit CPU that fits in a UEFI enabled motherboard.
Conversely, there are a few aberrations like a 64-bit Atom 'Bay Trail' CPU bundled with 32-bit UEFI.

What are you trying to do?

---

### Post by grahammechanical on 2015-03-27
Matthew Garret was a RedHat developers who did a lot of work on UEFI and secure boot. This is what he has to say about machines that have a 64 bit CPU but a 32 bit UEFI and the effort needed to make Linux compatible:

> [COLOR=#3E3E3E][FONT=Trebuchet MS]Having looked into what it'd take to implement it in Linux, I decided that hammering rusty nails through my feet would be a preferable use of time. Thankfully, I went drinking instead.[/FONT][/COLOR]

[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)

There is a Launchpad bug report on this with some people claiming that they have got around the problem by compiling their own 32 bit Grub EFI boot loader and installing that. They claim that it works but they miss the point made by Matthew Garret that trying to produce an ISO image with both a 64 bit grub EFI and a 32 bit grub EFI is possible but the likelyhood of it giving a successful install  is very small.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1341944](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1341944)

> [COLOR=#3E3E3E][FONT=Trebuchet MS]So, if you want a CD that'll boot on both BIOS and UEFI systems, you need two El-Torito images - one for BIOS, one for UEFI. Unfortunately, various BIOSes deal exceptionally badly with CD images that contain more than one El-Torito image. The most common failure case is to print a menu asking you to choose an option without labelling the options, but some will just fail outright. Thankfully, this is pretty much exclusively limited to 32-bit systems.[/FONT][/COLOR]

Of course, your request might not have anything to do with this subject but we do not know that as you have given very little information about what you are trying to do.

Regards.

---

### Post by checoimg on 2015-03-28
What I'm thinking of doing is install Ubuntu 32 bit on a USB and then making the installation of a EFI loader in the install to boot Ubuntu on a tablet. What I would love is to install it but the 32 bit version of ubuntu doesn't have EFI. In the opther hand I will start looking for a 64 bit tablet.

---

### Post by Vladlenin5000 on 2015-03-28
You're in for a big disappointment then.
The problem - again - is the 64-bit CPU plus the 32-bit UEFI. Keep that in mind, a _64-bit CPU_ for which you want a _64-bit OS_, only the UEFI must be 32-bit therefore it must be compiled for that purpose.
You can't use a 32-bit OS and if you plan to wait for a different, more compatible, hardware then good luck, you'll gonna need it.

---

### Post by checoimg on 2015-03-28
I maybe should produce the devide I want . :P No problem I accept my reality. Thanks

---

