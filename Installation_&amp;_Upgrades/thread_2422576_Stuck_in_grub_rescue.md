---
title: "Stuck in grub_rescue"
date: 2019-07-10
forum: Installation &amp; Upgrades
---

### Post by s6username6 on 2019-07-10
Hi there,


I'm stuck in Grub_rescue on my laptop. I can only boot from Ubuntu Live USB, but in the installation, he does not recognise my SSD. Normally you should change the SATA-mode in the bios, but there is a problem with getting into the bios of my Acer-laptop. Is there a way where I can my SSD on my live Ubuntu while my SATA-mode is in AHCI?
The goal is to format my SSD...


Thanks in advance


S.

---

### Post by oldfred on 2019-07-10
ACHI would be correct.

But many systems need UEFI update & SSD firmware update even if new to correctly see SSDs.

And if Acer is newer UEFI, after install you need to set "trust" in UEFI.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) &

---

