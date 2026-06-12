---
title: "Ubuntu 11.04 RAID 0 Installation Question"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by Strychnine213 on 2011-07-03
Hey all. So I figured it would be good to ask the experts before I attempted this.

       I have a Windows 7 x64 installation running in RAID 0 for work. I however love Linux and would like it back. I was wondering is it A:) Possible to safely install Ubuntu 11.04 to an existing RAID 0 installation, or B:) Is it possible to put Ubuntu 11.04 onto a separate hard drive and stick that into the loop. I preferably like option "B" the best, though I have some concerns. Because I am running a RAID 0 on Windows 7 would the Ubuntu install screw up the boot manager (because it is striped across two drives), or is it even possible run to dual boot with a RAID 0 configuration and a standard drive?!?

Thanks,
Strych

---

### Post by YesWeCan on 2011-07-03
My advice is to install Ubuntu and its boot-loader, Grub, both on a separate disk. Don't mess with the Windows disks. You may even want to disconnect your Windows disks as a precaution while you do it. Then you can set your bios to boot the Ubuntu disk first to get Grub. Or if you ever stop using Grub or Ubuntu you can still boot the RAID directly.

This leaves the issue of making Grub boot a Windows RAID0. I am sure it can but I don't have the recipe. Others will. :)
OR you can add the Ubuntu disk to your W7 boot-loader and then always boot the RAID from bios.

---

### Post by Strychnine213 on 2011-07-03
That's what I was thinking as well. I would like to have it on a separate disk so that if the RAID 0 goes down I still have my Ubuntu working. What I was pushing for (and what you said) is to install it on a separate disk and then have GRUB boot the Windows 7 RAID 0 partition. That being said I really appreciate the help.

---

