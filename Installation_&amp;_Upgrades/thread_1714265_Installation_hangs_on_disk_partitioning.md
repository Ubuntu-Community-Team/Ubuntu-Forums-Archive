---
title: "Installation hangs on disk partitioning"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by fernandezvara on 2011-03-25
Hi all,

Just bought a new computer that I will use as server:

Gigabyte 890GPA-UD3H motherboard
AMD Phenon II 1090T
16 Gb RAM
4 x Seagate 2Tb  hard disks


I tried to install Ubuntu server 10.04 and 10.10, both 64 bit, having similar results. 

Also I have tried enabling and disabling the RAID card.

On 10.04 installer hangs preparing disk partitioning phase at 43%, on 10.10 hangs at the same stage 45%.

Someone had the same issue?
Must I download something and apply before that phase?

Thanks in advance.

Antonio

---

### Post by ronparent on 2011-03-25
You must be using FakeRAID. Most likely an issue that prevents gparted on the distribution image that prevents it from seeing (or partitioning) raid drives. Just simply boot to the live cd and install kparts. The kpartx install will last only for the duration of the session so start install right off without leaving the session. The bug has been fixed upstream so if you choose to install gparted to the newly installed system it will probably automatically update so the bug is no longer present.

---

