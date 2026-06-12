---
title: "Ubuntu, Vista, and Dell"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by mattsnowboard on 2008-06-24
Ok, I'm about to install Ubuntu on my dell with media direct crap.

Anyway, I have the Dell EISA partition, then Vista, then the extended partition with the Dell media direct.

I want to know the best thing to do, can I install Ubuntu in the Extended partitiion that Media Direct is in?  So I leave that intact and avoid the issues with "the button" killing my MBR.  Or is there any way at all to get rid of Media Direct, and as long as that first Dell partition exists, the Media Direct button will safely boot into something (Ubuntu?) usefully and harmlessly?

I don't care much for Media Direct if I can avoid it, but I really want a stable system.

---

### Post by VMC on 2008-06-24
> **mattsnowboard said:**
> Ok, I'm about to install Ubuntu on my dell with media direct crap.

Anyway, I have the Dell EISA partition, then Vista, then the extended partition with the Dell media direct.

I want to know the best thing to do, can I install Ubuntu in the Extended partitiion that Media Direct is in?  So I leave that intact and avoid the issues with "the button" killing my MBR.  Or is there any way at all to get rid of Media Direct, and as long as that first Dell partition exists, the Media Direct button will safely boot into something (Ubuntu?) usefully and harmlessly?

I don't care much for Media Direct if I can avoid it, but I really want a stable system.

We do have a Dell subforum, where folks have answers to just this type of question.

But, do you want to keep your Vista mbr intact or are you willing to use Grub?
The ubuntu installer will make free space available on Windows partitions.

Here's a good link installing ubuntu after Vista has been installed. It has a lot of screenshots to help. It first uses Vista disk management tool in the begining and then shows pictures on using ubuntu with Grub as the boot loader:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

