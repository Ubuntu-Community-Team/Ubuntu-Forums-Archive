---
title: "UEFI - grub not installed on SSD"
date: 2016-05-14
forum: Installation &amp; Upgrades
---

### Post by gdesilva on 2016-05-14
Hi,

I am trying to do a clean install (NOT dual booting) of Ubuntu Studio 16.04 on a Toshiba Kira notebook (Intel i5 with 8GB RAM, 250GB SSD).

No problems installing the US in CSM mode and the system boots up without any issues.

However, when I select UEFI mode (with or without Secureboot), installation proceeds normally but when the machine restarts it cannot find grub and comes up with the message 'insert system disk in drive'. I have disabled Intel RST.

I would appreciate if anyone has any suggestions/comments/pointers to resolve this.

Thanks

---

### Post by oldfred on 2016-05-14
I believe newer Toshibas are now like Sony & HP. They violated a specific cause in the UEFI spec that says not to use description as part of boot. And of course only valid descption is "Windows Boot Manager".

There are several work arounds. All UEFI system boot a hard drive or fallback entry at /EFI/Boot/bootx64.efi. Windows typically makes that file the same as the standard Windows efi boot file, but we can make it be shimx64.efi to boot Ubuntu.

If only booting Ubuntu you can also just change the descption from ubuntu and make the entry for "Windows Boot Manager" be actually /EFI/ubuntu/shimx64.efi. 

I suggest doing both, but either way you then do not boot ubuntu in UEFI but either hard drive or Windows UEFI entries.

Details buried in link in my signature somewhere.

Vendors typically use similar UEFI for all models and modify for options, so solution for Toshiba applies to most models.
       Toshiba Satellite - turned Secure boot off in Boot-Repair update
[http://ubuntuforums.org/showthread.php?t=2317643](http://ubuntuforums.org/showthread.php?t=2317643)
Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair
[/URL]
 Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba Satellite P55-A (UEFI) [SOLVED] Trouble installing Xubuntu 14.04 - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Toshiba shows BCD entry
[http://ubuntuforums.org/showthread.php?t=2259331](http://ubuntuforums.org/showthread.php?t=2259331) 

[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]
[/URL]

---

### Post by gdesilva on 2016-05-14
@oldfred, Because I wiped out the entire SSD (created a new gpt partition table) prior to installing Ubuntu Studio, my /EFI shows only one entry which is 'ubuntu'. I created another directory called Boot and copied all files under /EFI/ubuntu to /EFI/Boot and then renamed grubx64.efi to bootx64.efi.

Now the machine boots OK.

Many thanks for your help.

---

### Post by oldfred on 2016-05-14
Glad that worked. :)

---

