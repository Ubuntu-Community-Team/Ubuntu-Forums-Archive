---
title: "problem updating grub!!!"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by davidtuti on 2010-02-04
Hi,

I have kubuntu 9.10. This morning I update the Grub v.1.98 experimental and now when I reboot and I can't  boot with ubuntu or windows xp.

In ubuntu gives me : "Error:file not found" and with XP gives me "Error: invalid file name".

Pleaseee any help!?
Thanks a lot and sorry for my english!

---

### Post by Azteka on 2010-02-04
try this [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) 1-st or 3-rd methods

---

### Post by ptviperz on 2010-02-04
> **davidtuti said:**
> Hi,

I have kubuntu 9.10. This morning I update the Grub v.1.98 experimental and now when I reboot and I can't  boot with ubuntu or windows xp.

In ubuntu gives me : "Error:file not found" and with XP gives me "Error: invalid file name".

Pleaseee any help!?
Thanks a lot and sorry for my english!

Same thing happened to me, looks there was a typo in the update; to fix simply highlight the entry you want to boot and press 'e' This should give you the options for that entry. In mine, the linux kernel specified was missing the 'c' at the end of generic

Add the c and hit ctrl-x to boot

In my windows install, the '1' was missing from the last line, chainloader +1

---

