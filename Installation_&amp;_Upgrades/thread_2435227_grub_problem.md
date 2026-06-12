---
title: "grub problem"
date: 2020-01-17
forum: Installation &amp; Upgrades
---

### Post by sysone on 2020-01-17
On a laptop with Win 10 I installed Ubuntu 18.04 with no apparent problem. 
But now it only boots in Windows.
I can boot in the installation item but don't know how to repair grub.

---

### Post by oldfred on 2020-01-17
Both Windows & grub on major updates reset default boot order, if UEFI. Or reinstall to MBR if BIOS.
Windows also typically turns on Windows fast start up. So even if you turned it off before, you need to turn it off again.

If UEFI can you boot Ubuntu entry in UEFI boot menu?

If not:
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by sysone on 2020-01-19
[B]Thanks[URL="https://ubuntuforums.org/member.php?u=852711"][COLOR=#C61919][B] oldfred,
I used gparted to delete the new Ubuntu  and reinstalled it .
Things worked out fine
[/B][/COLOR][COLOR=#C61919]****[/COLOR][/URL][/B]

---

