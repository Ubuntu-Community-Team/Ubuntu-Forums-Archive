---
title: "How to dual-boot Ubuntu and Win 7 on same drive?"
date: 2021-02-16
forum: Installation &amp; Upgrades
---

### Post by linuxtecher on 2021-02-16
Hello all,

I would like to know how to dual boot Ubuntu and Win 7 on an same SSD drive?

Please help me.

Thanks.

---

### Post by yancek on 2021-02-16
The first step would be to boot into windows 7 and use the disk management tool to shrink the largest windows partition to leave unallocated space for Ubuntu.  If the computer BIOS is Legacc  (not EFI) then you should not have any problem.  If it does have EFI capability, you need to make sure when you select the boot USB or DVD that it is under the Legacy/CSM option and not EFI.  There are numerous tutorials on this such as the one at the link below.

[https://www.lifewire.com/ultimate-windows-7-ubuntu-linux-dual-boot-guide-2200653](https://www.lifewire.com/ultimate-windows-7-ubuntu-linux-dual-boot-guide-2200653)

Do the rest of us a favor and don't go online with your insecure and unsupported windows 7.

---

