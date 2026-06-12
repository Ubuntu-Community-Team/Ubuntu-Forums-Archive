---
title: "Newbie Install Advice Please."
date: 2005-06-15
forum: Installation &amp; Upgrades
---

### Post by BenM on 2005-06-15
Hi, I am currently trying to install Ubuntu on an old system that I have lying around. It is an old Dell Inspiron 433 Celeron, 4 gig hard drive (2 gig free), 256 MB RAM currently running Windows 98.

Here are the steps I have taken so far. Downloaded both the install and live CDs. Verified their checksums and burned them. Double checked my BIOS for boot order (floppy, cdrom, hard drive).

I have no problem using the live disk. It boots up no problem (which I think confirms boot order), but have not had any luck with the install CD. While it looks like the drive is working prior to loading windows, it just goes on to boot windows. I have tried serveral burns of the install CD in case one of them was bad, but no luck.

Any advice would be appreciated.

---

### Post by kiddo on 2005-06-15
Please clarify:> While it looks like the drive is working prior to loading windows, it just goes on to boot windows. I have tried serveral burns of the install CD in case one of them was bad, but no luck Do you mean
[list]
[*]you can't *boot* the installer cd at all? or   
[*]after the installation, windows still boots instead of ubuntu 
[/list] Is this supposed to be a dualboot system ? (I don't recommend, especially since W98 is pretty useless :))

---

### Post by BenM on 2005-06-15
Hi, the problem is that I can't boot the installer CD. It looks like the CD ROM drive is active, but nothing happens.

I am not trying for a dual boot. Since I have an extra system, i wanted to play around with a Linux distro and choose Ubuntu. Do I need to wipe the HD prior to the install? or is that possible as a part of the install.

Thanks.

---

### Post by kiddo on 2005-06-15
Since the livecd boots and the install doesn't, well.. I don't know. The partitioning can be efficiently done during the ubuntu install. I don't know how to solve your problem however.

---

### Post by Joeb on 2005-06-15
[QUOTE=BenM]Hi, the problem is that I can't boot the installer CD. It looks like the CD ROM drive is active, but nothing happens.

I am not trying for a dual boot. Since I have an extra system, i wanted to play around with a Linux distro and choose Ubuntu. Do I need to wipe the HD prior to the install? or is that possible as a part of the install.

Thanks.[/QUOTE]

If you put the install CD in another computer, can it be read?  It might just be that you have a bad CD.

You do not need to wipe the HD prior to installation, you can tell the installer to do that for you.

---

### Post by alastair on 2005-06-15
Don't really know.

You could try booting the installer via :

linux vga=791

perhaps. Or maybe :

linux ide=nodma

---

