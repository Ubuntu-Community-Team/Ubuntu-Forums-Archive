---
title: "Does ubuntu working fine if i cloned installation from external usb to SSD hard disk"
date: 2018-05-16
forum: Installation &amp; Upgrades
---

### Post by merocom on 2018-05-16
[COLOR=#111111][FONT=Ubuntu]- Now i'm installing ubuntu 18.04 on an external usb. 
- Cloned full ubuntu installation from usb to the second SSD. 
- It's booting normally but to GNU GRUB screen .

[/FONT][/COLOR]grub> ls

hd0 (hd0,gpt1) (hd0,gpt2) (hd0,gpt3) (hd0,gpt4) hd1 (hd1,gpt1) (hd1,gpt2) (hd1,gpt3) (hd1,gpt4)

grub>boot
 
You need to load kernel first

how to fix it error ??

---

### Post by oldfred on 2018-05-16
UEFI or BIOS installs?
What brand/model system?

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

