---
title: "No GRUB with Windows 8 and Xubuntu 12.04 dual boot"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by jamesfbays on 2013-08-20
I installed Xubuntu 12.04 alongside Windows 8 (with secure boot on a UEFI based PC) hoping for a dual boot system. But the GRUB menu doesn't appear at startup. The computer boots straight into Windows. I've Googled the problem and searched this forum (and mucked around in the bios) with little luck. Does anyone know how to get my dual boot / grub to work? If so, please answer, and I will be eternally in your debt. Thanks.

---

### Post by Bucky Ball on 2013-08-20
*Thread moved to **Installation & Upgrades**.*

As far as I know, you can have UEFI or GPT, not both. If you installed with UEFI on then that is how you will boot, Grub won't displace that. You can't mix and match. 

Oldfred is the guru of all things UEFI round here so hopefully he will spot this eventually. ;)

---

### Post by fantab on 2013-08-20
> **Bucky Ball said:**
> As far as I know, you can have UEFI or GPT, not both. If you installed with UEFI on then that is how you will boot, Grub won't displace that. You can't mix and match. 

Actually, its the other way round. UEFI only works with GPT. Windows will only boot in EFI with GPT, and only UEFI from GPT. While Linux can boot from GPT in 'legacy mode' with a separate /boot partition.


@**jamesfbays**: USE [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair") utility to fix the boot issue you are having. After you run Boot-Repair run the 'recommended repair'. If the problem persists then post the link that 'Boot Info Summary' generates, so that we can check whats going on at the boot.

Good Luck...

---

### Post by Bucky Ball on 2013-08-20
> **fantab said:**
> Actually, its the other way round. UEFI only works with GPT. Windows will only boot in EFI with GPT, and only UEFI from GPT. While Linux can boot from GPT in 'legacy mode' with a separate /boot partition.

Thanks for that. Learn something everything day and I openly confess to knowing little to nothing about EFI as never had the need to dabble. So now I know something. ;)

Definitely Boot Repair then, as about the only other thing I know is that BR now fixes UEFI/GPT issues as well. As mentioned, post Bootinfoscript results if no success.

---

### Post by jamesfbays on 2013-08-26
Thanks fantab. Boot Repair told me which iso version I needed to install and then fixed grub. (Now if I could only figure out how to mark this thread as "Solved")

---

### Post by Bucky Ball on 2013-08-26
Simply follow the link in my signature. ;)

---

