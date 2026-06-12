---
title: "Boot error"
date: 2023-01-03
forum: Installation &amp; Upgrades
---

### Post by anjublaxxx on 2023-01-03
Hello. I'd like help. I've tried installing Ubuntu alongside windows for dual boot but can't get access to either OSs upon installation completion.
I've done the boot repair which summary is stored here [https://pastebin.ubuntu.com/p/vgRZ7TNm2n/](https://pastebin.ubuntu.com/p/vgRZ7TNm2n/)

I will appreciate your input

---

### Post by tea for one on 2023-01-03
You have Windows 8/10 in Legacy mode and Ubuntu in UEFI mode.
Mixed modes on one disk is inherently unstable.
More info here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You could try the suggested repair (lines 269 - 283 in the report) but it may not be successful.

In order to have a robust dual boot system on one disk, you should consider installing both Windows 10 and Ubuntu in UEFI mode with GPT.

However, before you do anything, make sure that you have backups of your irreplaceable personal data?

---

### Post by yancek on 2023-01-03
The suggested repair to reinstall Grub in Legacy mode should work.  You would need to reboot with Legacy mode enabled and do a Legacy install of Grub since windows is in Legacy mode.  A Griub install in UEFI mode will not boot windows installed in Legacy mode.  Since both windows and ubuntu are on the same drive, you cannot boot each separately from the BIOS so you need to either reinstall Grub in Legacy mode or reinstall Ubuntu in Legacy mode.

---

