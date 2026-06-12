---
title: "Computer freeze -Upgrade to 14.04 LTS from 12.04"
date: 2014-10-02
forum: Installation &amp; Upgrades
---

### Post by hila2 on 2014-10-02
[FONT=arial]Hi, [/FONT]
[FONT=arial]I would appreciate any help :-)
[/FONT]
[FONT=arial]I did upgrade from 12.04 to 14.04 I have dual with xp and intel graphic card, Grub menu. After I did the upgrade it got black screen when I logged it and clicked on any thing, when the computer got black screen its sound like the computer still on, I had to restart the computer and it happened all the time, also I had message saying   “System program problem detected" so I was looking to fix it and found how to remove it so I did and the messaged been removed but the problems with crashing to black screen still was going on. [/FONT]
[FONT=arial]I found another help and did this one :"Boot into recovery mode (or you can actually just hit ctrl + alt + f1 to drop into a shell from your black screen, which is what I did)[/FONT]
[FONT=arial]type in: sudo apt-get remove lightdm[/FONT]
[FONT=arial]sudo apt-get install gdm[/FONT]
[FONT=arial]sudo shutdown -r 0 "[/FONT][FONT=arial]
[/FONT]
[FONT=arial]So it did helped me with that that I didnt had to restart the computer each time it crashed and only had to log in each time instead.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]When I use only chromium I can stay long with out  the crashing but clicking on any thing else cause it to crash.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Intel® Core™2 CPU 4400 @ 2.00GHz × 2 


Intel® 945G x86/MMX/SSE2


32-bit
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I looked for errors', 'warnings', or 'failed' /var/logs for 'boot.log', 'dmesg', kern.log and this what iv found [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]dmesg:
[/FONT]
[FONT=arial]

[    0.161083]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.161085] ACPI _OSC control for PCIe not granted, disabling ASPM


[   18.051906] init: failsafe main process (624) killed by TERM signal


errors=remount-ro
[   16.237639] lp: driver loaded but no devices found
[   16.238703] parport_pc 00:09: reported by Plug and Play ACPI


kern.log:


Sep 29 12:57:58 hila-945GCMX-S2 kernel: [    0.161093]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d


Sep 29 20:00:31 hila-945GCMX-S2 kernel: [    8.962775] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Please can you help me? I dont know what to do :-(  [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Thanks [/FONT]

---

### Post by hila2 on 2014-10-03
Hi again 

I didn't got any help so I didnt had any choice and continue to try to solve it, so one of the things I did was to update my intel driver with intel installer, after that I had some more problems but all gone now, the only problem I have now and its really annoying is that the computer get freeze each time I click on the dash home, or on firefox or even when I did search on log file :mad: 

Please help me :shock:

Thanks

---

