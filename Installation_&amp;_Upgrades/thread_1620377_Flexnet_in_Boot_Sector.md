---
title: "Flexnet in Boot Sector"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by haok on 2010-11-13
Hi All,

Just wanted to share my experience with fresh install of of XP and 10.10 yesterday. Hopefully, it will assist someone else.

I run a dual boot system with XP (installed first) and Ubuntu on the same HDD. System is a HP nw8440 laptop.

After running the original HP XP install with Creditentials Manager, Backup tools etc. XP was running fine. Also, 10.10 installed without issue. Grub2 menu was all good as well. 

When logging back into XP and then after a restart however I lost Grub2. System showed no sign of the grub2 menu and refused to boot any OS. XP had overwritten the MBR. 

Using the Live CD I restored the grub2 cfg boot sector file. After restoration, Terminal reported flexnet files in the boot sector. I then removed all proprietary HP apps in the XP install. After this and another round of Grub2 restoration the system is working fine. 

I haven't had this issue before with any previous install of XP/Ubuntu dual boot systems.

---

