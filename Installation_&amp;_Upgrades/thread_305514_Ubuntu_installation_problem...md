---
title: "Ubuntu installation problem.."
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by xiliax on 2006-11-23
Hello!
I have a strange problem (at least i think it's strange). So.. I installed Ubuntu 6.06 and everything was ok, then i formatted and installed Kubuntu 6.06, after that I did some partitioning (increased size of swap partition) and formatted again .. and I cannot install ubuntu ever since.. system hangs after I choose to manually do my partitioning in the setup..it's not the cd, I tried like 3-4 copies and it always hangs at the same place, however, kubuntu installation passes without any problems...

---

### Post by NotJustANewbie on 2006-11-23
:confused: If you don't mind losing data (ie Kubuntu), format your whole hard drive again and use different sizes for a fresh Ubuntu install.

Also try [GParted Live Cd]("http://gparted.sourceforge.net/livecd.php") instead of the Ubuntu partitioner to partition your hard drive before you install Ubuntu - what I mean is use that live cd instead of the Ubuntu cd to do the partitioning part of your Ubuntu installation.
Gd luck 8)

---

### Post by the_joker on 2006-11-23
> **NotJustANewbie said:**
> :confused: If you don't mind losing data (ie Kubuntu), format your whole hard drive again and use different sizes for a fresh Ubuntu install.

Also try [GParted Live Cd]("http://gparted.sourceforge.net/livecd.php") instead of the Ubuntu partitioner to partition your hard drive before you install Ubuntu - what I mean is use that live cd instead of the Ubuntu cd to do the partitioning part of your Ubuntu installation.
Gd luck 8)
I think the problem is that unless you give Ubuntu free reign over your disks, the Live CD installer will not proceed. I have had the same fault - installation step 5, partitioning disks. When partitioning manually, the installer freezes, and simply seems to freeze.

In this situation, I don't think re-creating partitions will help - of course, I could be wrong, as I have not tried it myself - I prefer to keep my data intact ;)

I still haven't found a solution for this though.

---

