---
title: "Multi-Boot w/Win XP"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by ckasprzak on 2006-07-19
I have a quick question here.  

I want to dual boot with Windows XP but have Ubuntu on one Hard disk and XP on another.  

Now if I first install Ubuntu on drive x, then install XP on drive y will XP destroy my lilo or grub install if I have my linux disk as the first sata drive?

Thanks in advance!

---

### Post by wahman143 on 2006-07-20
> **ckasprzak said:**
> Now if I first install Ubuntu on drive x, then install XP on drive y will XP destroy my lilo or grub install if I have my linux disk as the first sata drive?

Thanks in advance!
Yes, windows will clobber your bootloader if you install it second.  Best practice is to install 'doze first and then Ubuntu, that way you don't have to worry about fixing the bootloader!

Cheers,
W.

---

### Post by ckasprzak on 2006-07-30
I've been checking into a few options that you can use the ntldr instead of the linux one.

But do you have to use lilo to go this route?

---

