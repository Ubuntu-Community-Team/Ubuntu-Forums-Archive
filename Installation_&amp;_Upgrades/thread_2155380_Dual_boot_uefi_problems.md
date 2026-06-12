---
title: "Dual boot uefi problems"
date: 2013-06-18
forum: Installation &amp; Upgrades
---

### Post by amiacamal on 2013-06-18
Hi all,

I recently bought an Inspiron 15 - 3521 preinstalled with windows 8. I have disabled secure boot and installed ubuntu 13.04  but I'm having a problem. If I just let it boot normally all I get is 
> 
PXE-M0F: Exiting PXE ROM
error: file '/boot.grub.i386-pc/normal.mod' not found
grub rescue> _


However if I spam F12 while booting I can select "Windows Boot Manager" which will boot me into grub as normal.
If I enable secure rom it says both windows and ubuntu are disabled by security setings.

My question is, How do I get my machine to load to grub instead of having to go into BIOS every time?
Thanks :)

---

### Post by byStanderone on 2013-06-18
...if i recol , read something about fast boot in win8...this option got to be disabled in win8, for ubuntu to mount properly.

---

### Post by amiacamal on 2013-06-18
Success! Thanks for that!

---

