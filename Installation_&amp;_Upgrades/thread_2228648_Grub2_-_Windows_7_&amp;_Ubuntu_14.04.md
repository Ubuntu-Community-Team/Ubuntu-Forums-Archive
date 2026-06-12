---
title: "Grub2 - Windows 7 &amp; Ubuntu 14.04"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by karl.dean.parry on 2014-06-08
Hi all,

I hope someone can help me with this. I have 3 HDD 

sda - windows 7
sdb - ubuntu 14.04
sdc - no OS

I just formatted sdb and put a fresh install of Ubuntu in it but now Grub does not recognise Windows 7. Here is the boot info. Any help appreciated

[URL="http://paste.ubuntu.com/7615035/"]http://paste.ubuntu.com/7615035/ 
[/URL]
Thank You

---

### Post by ubfan1 on 2014-06-08
So you seem to have an UEFI machine booting Win7 .  No bootloaders in the MBRs of your disks, so you must use the EFI to boot.  Not only did grub not find any Windows OS, the EFI boot menu did not either (unless steamos is windows???).   Your EFI partition seems to be sdb2, but I see only ubuntu files there, no Windows.  What mode are you trying to use, legacy or UEFI?  Is this a downgraded Win 8 machine?  How were you originally booting Windows?

---

