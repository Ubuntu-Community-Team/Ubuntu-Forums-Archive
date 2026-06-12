---
title: "Is it still true - secure boot must be off to dual boot via Grub?"
date: 2016-06-12
forum: Installation &amp; Upgrades
---

### Post by Geoffrey_Arndt on 2016-06-12
I've read secure boot must be disabled if dual-booting via Grub . . . is that still true?   What is the standard Windows 8-10 bootloader called?

Thanks.

---

### Post by oldfred on 2016-06-12
You can dual boot from UEFI boot manager, often one time boot key like f10 or f12, if you have UEFI Secure boot on.

It is only dual booting from grub menu that was issue.
Something about the chain of security from grub back to Windows is lost. They were making some improvements with 16.04, but do not know if it now works or not. 

I do not use UEFI secure boot and consider it primarily Marketing from Microsoft. They have a poor reputation on security from virus', but Secure Boot does not change that. But most users see new Windows with "Secure Boot" and assume it is better. 
And only major Boot virus was actually from Sony in implementing DRM so you could not play music without a license.
Some time in future may have to turn on Secure boot, but not now.

---

### Post by lliseil on 2016-06-12
Thanks oldfred for making it clear here.

> only major Boot virus was actually from Sony in implementing DRM.

Well it all depends whose "security" they're talking about!

EDIT: 
Ours, or theirs security (in case not specific for some)

---

