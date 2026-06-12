---
title: "Unable to dualboot with Win10 on RAID0"
date: 2020-05-03
forum: Installation &amp; Upgrades
---

### Post by vishnumrao on 2020-05-03
Storage on my desktop is RAID0 on 4x64 GB SSDs. The RAID0 was created using the UEFI menu in the BIOS. The desktop currently has Windows10 on it. The intent is to dualboot Ubuntu 20.04. I booted the liveUSB but the installer does not see the Windows10 installation. Only option offered is install Ubuntu 20.04. In the advanced/ customer install option, it does see the the RAID0 (dm-0) and the Windows partitions. 

Just because i had an Ubuntu 18.04 liveUSB, I tried it as well. Same issue. Any ideas on what could be wrong?

---

### Post by CelticWarrior on 2020-05-03
First things first, are you booting the live session in the same mode as the Windows installation? UEFI or BIOS?

---

### Post by vishnumrao on 2020-05-03
I don't recall what mode Windows was installed. So I used some instructions [here]("https://www.tenforums.com/tutorials/85195-check-if-windows-10-using-uefi-legacy-bios.html") to check. BIOS Mode is UEFI. Secure Boot State is unsupported.

Note that the liveUSB was created with Rufus v3.10. It does say the default works for both UEFE & BIOS. On my machine at the boot menu, I get two options. UEFI and USB (I guess legacy mode). I have tried both options. Installer does not see Windows10 in either case.

---

