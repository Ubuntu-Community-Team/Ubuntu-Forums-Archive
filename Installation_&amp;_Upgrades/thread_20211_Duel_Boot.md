---
title: "Duel Boot"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by Ernest S Harris on 2005-03-15
I have loaded Ubuntu with Windows XP Pro. When I loaded it, a duel boot (GNU Grub) was created in my MBR. How do I get this out so that I dont get asked which system I want to boot into? :???:

---

### Post by Ptero-4 on 2005-03-15
[QUOTE=Ernest S Harris]I have loaded Ubuntu with Windows XP Pro. When I loaded it, a duel boot (GNU Grub) was created in my MBR. How do I get this out so that I dont get asked which system I want to boot into? :???:[/QUOTE]
 boot to a Win9x CD (AFAIK WinXP doesn't handle dos fdisk correctly) and run "fdisk /mbr" (w/o the quotes). This should remove grub. After that you'll need a boot disk to boot to ubuntu.

---

### Post by Buffalo Soldier on 2005-03-15
[QUOTE=Ernest S Harris]I have loaded Ubuntu with Windows XP Pro. When I loaded it, a duel boot (GNU Grub) was created in my MBR. How do I get this out so that I dont get asked which system I want to boot into? :???:[/QUOTE]
 Just out of curiosity, why didn't you want to be asked which system to boot into?

---

### Post by Xian on 2005-03-15
[QUOTE=Ernest S Harris]How do I get this out so that I dont get asked which system I want to boot into?[/QUOTE]
You do realize that if you "get this out" you will only be able to boot into Windows without some other means....?

---

