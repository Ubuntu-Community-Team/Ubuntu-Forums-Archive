---
title: "Grub error after formatting the hdd to NTFS"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by meazz1 on 2009-12-05
I bought a laptop with Windows 7. I than installed Ubuntu 9.10 as a dual boot. I chose all the default option when I was installing Ubuntu 9.10.

Today I decided to format the hdd with NTFS, so I used gparted to do so. After formatting to NTFS, I installed Win 7 to factory default.
Every time I try to restart pc, I get Grub error.

How do I deleted grub from the hdd?

---

### Post by lindsay7 on 2009-12-05
So is the only thing on your computer windows 7 and the grub file?  If so try this,

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by presence1960 on 2009-12-05
> **lindsay7 said:**
> So is the only thing on your computer windows 7 and the grub file?  If so try this,

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

+1

GRUB is still on MBR. Here is another [link]("http://ubuntuforums.org/showthread.php?t=1014708") to the same info, I just prefer material from our community over MS's.

That will put windows bootloader on MBR.

---

### Post by meazz1 on 2009-12-05
Thanks to you both for your reply.

lindsay7 - I tried your suggestion and got windows 7 back. Thanks

---

