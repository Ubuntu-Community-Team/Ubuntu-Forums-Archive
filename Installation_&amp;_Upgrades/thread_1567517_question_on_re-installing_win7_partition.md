---
title: "question on re-installing win7 partition"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by D3mon_Spawn on 2010-09-03
hey everyone! I currently have two partitions on my laptop right now: Win7 and Ubuntu 10.04. The Win 7 partition that I have is the default one that came with my laptop and all its bloatware. I want to have a fresh install on this Win 7 partition; so my question is even though I have grub as my boot loader if I do a fresh install of win7 on the already existing win7 partition will that get rid of grub? I still want to keep grub as my boot loader booting up ubuntu first.

---

### Post by ronparent on 2010-09-03
Installing Win 7 will overwrite the grub boot loader. That is fixable from a live cd. See the attached for instructions: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

Post again if you need more help.

---

### Post by Mark Phelps on 2010-09-03
> **D3mon_Spawn said:**
> ... The Win 7 partition that I have is the default one that came with my laptop and all its bloatware. I want to have a fresh install on this Win 7 partition

So you have a Win7 installation DVD?  

Usually, the CDs that come with preinstalled system only do full system restore -- including the "bloatware" that you have now.  

Either way, the MBR is going to get overwritten by the Win7 restore/reinstall.

---

