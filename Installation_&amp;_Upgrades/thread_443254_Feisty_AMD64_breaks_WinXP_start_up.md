---
title: "Feisty AMD64 breaks WinXP start up"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by pensador82 on 2007-05-14
I decided to make a clean install of Feisty and this time I went with the AMD64 version (since I have a 64-bit AMD CPU). The installer apparently does not recognize the presence of Windows XP Pro and it seems to completely mess up the master boot record.

I have 2 HDs: Windows is on a SATA hard disc and I wanted to install Ubuntu on a PATA hard disc.

I tried to fix it by editing the GRUB loader but it only resulted in frustrations.

Is there a solution to this problem?

---

### Post by pensador82 on 2007-05-15
Anyone?

---

### Post by sparrowhawk on 2007-05-16
I am not very hot on boot loaders or partitions, that is why I disconnected my Windows drive and did a clean install to my other disc. This works because my bios allows me to press F12 for boot options. Not sure if this helps you at all !

---

### Post by pensador82 on 2007-05-16
Thanks for the reply, sparrowhawk. I didn't think about that solution. It's not very elegant but I'm sure it would work. :)

---

