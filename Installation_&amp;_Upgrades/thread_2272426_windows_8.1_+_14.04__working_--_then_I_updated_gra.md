---
title: "windows 8.1 + 14.04  working -- then I updated graphics drivers on Win 8--&gt; problem"
date: 2015-04-06
forum: Installation &amp; Upgrades
---

### Post by xigen on 2015-04-06
My system was working just fine with Windows 8.1 + Ubuntu 14.04

Then I updated the invidia graphics on windows 8.1: it asked for a reboot, and hung for 5+ minutes

Upon reboot I could no longer access win 8.1 or Ubuntu 14.04.

I tried boot repair:
[ATTACH=CONFIG]261127[/ATTACH]

I then tried to repair grub using a 14.04 usb 
[ATTACH=CONFIG]261128[/ATTACH]

How would you suggest I get my system/grub back?

Best,

MW

---

### Post by oldfred on 2015-04-06
Boot Ubuntu installer with Boot-Repair in UEFI mode not BIOS/CSM/Legacy mode.

Then post link to summary report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by xigen on 2015-04-06
hmmmm... it looks like I am booting in UEFI mode (see pics)

thoughts?

[ATTACH=CONFIG]261130[/ATTACH][ATTACH=CONFIG]261131[/ATTACH][ATTACH=CONFIG]261132[/ATTACH][ATTACH=CONFIG]261133[/ATTACH]

MW

---

### Post by oldfred on 2015-04-06
Do you get grub menu or BIOS screen?

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If booted in UEFI mode then run summary report.

---

