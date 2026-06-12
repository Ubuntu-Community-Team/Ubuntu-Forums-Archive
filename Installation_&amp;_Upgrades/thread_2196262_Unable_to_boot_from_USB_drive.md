---
title: "Unable to boot from USB drive"
date: 2013-12-28
forum: Installation &amp; Upgrades
---

### Post by harshnisar on 2013-12-28
[COLOR=#000000][FONT=HPRegular]I am trying to boot Ubuntu 13.10 from a [/FONT][/COLOR][COLOR=#5F76A5][FONT=HPRegular]**USB**[/FONT][/COLOR][COLOR=#000000][FONT=HPRegular] Drive. I was expecting a regulation procedure: BIOS>BOOT-order-tweak>boot-from-[/FONT][/COLOR][COLOR=#5F76A5][FONT=HPRegular]**USB**[/FONT][/COLOR][COLOR=#000000][FONT=HPRegular]. But it didn't work. I recently upgraded from a 7 year old laptop, and am not familiar with either UEFI or SecureBoot or how these change anything. From first impressions of what research i could do, the combination of said unfamiliar standards help avoid malware from doing there thing, help Windows to boot super fast and are compatible with newer versions of popular Linux distrbutions. So ideally one should be able to boot into described Linux distro from [/FONT][/COLOR][COLOR=#5F76A5][FONT=HPRegular]**USB**[/FONT][/COLOR][COLOR=#000000][FONT=HPRegular] w/o disabling SecureBoot or enabling Legacy anything. The problem seems quite trivial, as it is not being discussed at all. [/FONT][/COLOR][COLOR=#000000][FONT=HPRegular]What am I doing wrong? This also worries me a bit, because I was thinking of moving windows recovery to an external drive and freeing up the valuable space from my tiny SSD (and hopefully installing another OS there), and if I can't boot from [COLOR=#5F76A5]**USB**[/COLOR]...!!
About Linux, can anyone also let me know if installing software not provided by HP voids my warranty?[/FONT][/COLOR]

---

### Post by oldfred on 2013-12-28
HP phone support may say that warranty is voided, but I think in many countries that would not be legally enforceable. 

Best to make full image copies of efi partition and Windows install, so you can restore later.
Is this an Ultrabook with small SSD and dual video? If so more info in link in my signature.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

