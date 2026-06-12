---
title: "NTLoader as bootloader"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by obsrv on 2008-06-19
How do I use ntldr (ntloader) as my main bootloader to boot not only Windows XP but also KUbuntu 8.04?

---

### Post by logos34 on 2008-06-19
Here (automatic and manual method):

[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)
[http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why](http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why)

The question, though, is why?  Grub is better, and if you don't want to see it at boot you can hide it.  If you ever revert back solely to windows, you can easily restore the latter's bootloader--it's not like grub is going to mess anything up.

---

### Post by obsrv on 2008-06-20
Using grub I cannot boot into my Windows XP x64. I tried with KUbuntu, Ubuntu and Gentoo. But this morning I tried OpenSUSE 11, and its bootloader loaded my Windows XP x64. I think they use gfxboot or smth. Is it grub2?

---

### Post by logos34 on 2008-06-20
> **obsrv said:**
> Using grub I cannot boot into my Windows XP x64. I tried with KUbuntu, Ubuntu and Gentoo. But this morning I tried OpenSUSE 11, and its bootloader loaded my Windows XP x64. I think they use gfxboot or smth. Is it grub2?

Grub2 is still under development, so it's using grub 0.97.  

I never had a problem dual-booting my XP Pro x64 with grub. 

Post your disk layout and grub menu:

# fdisk -l 

cat /boot/grub/menu.lst

---

