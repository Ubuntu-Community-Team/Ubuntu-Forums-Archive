---
title: "WUBI Ubuntu Upgrade"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by Mil Doc Jr on 2010-03-05
I have a Windows 7 laptop with 64 bit architecture.  I want to install Ubuntu 9.10 on it in hopes to upgrade to 10.04 when it comes out in April-ish.  If I do the upgrade through apt will it overwrite the MBR or will it just upgrade the system and I'll still have the MBR.  I would to dual-boot with grub but I have a computer illiterate wife and a 5 y/o son who likes to mash keyboard keys, which is why I'm going this route.  Has anyone upgraded from intrepid to jaunty or jaunty to karmic using this method, please let me know how it worked or if I should just wait until Lucid comes out.

---

### Post by gordintoronto on 2010-03-05
When you install using Wubi, you get a dual-boot system, it just avoids partitioning of the hard drive.  Ubuntu does not run from within Windows, you choose at boot time.

If you want to run from within Windows, you can use virtualization, such as Virtualbox. A few issues back, Full Circle Magazine had a story about installing Ubuntu within Virtualbox in Windows.

If you do install using Wubi, intending to upgrade, make sure you give Ubuntu more than the minimum amount of space. I would go with at least 25 GB, but that's more than you need.

---

