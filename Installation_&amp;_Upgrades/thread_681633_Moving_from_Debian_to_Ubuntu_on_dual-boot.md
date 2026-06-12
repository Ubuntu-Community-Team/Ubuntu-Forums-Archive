---
title: "Moving from Debian to Ubuntu on dual-boot"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by ydiaz on 2008-01-29
Hi guys, I have an Aspire 1400 laptop with a dual-boot WinXP and Debian. I've decided to move to Ubuntu and give it a try, see if I like it better. I have an fat32 partition on hda1 with WinXP, an ext3 partition on hda2 and a swap partition so I shouldn't need to mess too much around. Now my system is correctly configured for dual-booting windows and Debian through LILO, when I install Ubuntu, will GRUB replace LILO on the MBR? Do I need to specify anything on installation for it to recognize the WinXP option?

Thanks in advance!

---

### Post by jeffus_il on 2008-01-29
Should work fine, I recommend you download and burn a copy of [supergrubdisk]("http://geocities.com/supergrubdisk/")
in case of an emergency.

---

