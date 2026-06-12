---
title: "Ubuntu 18.04 does not see PCle SSD with SATA mode set to AHCI on Acer Aspire 7"
date: 2019-10-16
forum: Installation &amp; Upgrades
---

### Post by xarctus on 2019-10-16
I have Acer Aspire 7 A715-71G with newest BIOS version installed. I am trying to do Windows 10 Ubuntu 18.04.3 dual boot.


  I have successfully installed Windows on my SSD (ADATA SX8200 Pro  512GB) and created an empty partition for Ubuntu. I have disabled fast  boost in Windows, secure boot in Bios and I have SATA mode set to AHCI.
  But when I try to install Ubuntu from USB I do not see the SSD drive...


  I was trying tons of solutions online but nothing helped. Let me know if you need more information.


  I'll be very grateful for any help.
  Thanks,
xarctus

---

### Post by oldfred on 2019-10-16
Many also need SSD firmware update.

And if Windows is installed, did you turn off Windows fast start up?

Was this using RAID 0 with two drives?
You then have to erase meta-data on drive.
Acer S7 14.04 & Windows 8.1 RAID
[http://askubuntu.com/questions/590644/install-ubuntu-14-04-2-lts-alongside-windows-8-1-dual-boot-on-raid-acer-s7-quest](http://askubuntu.com/questions/590644/install-ubuntu-14-04-2-lts-alongside-windows-8-1-dual-boot-on-raid-acer-s7-quest)
acer aspire s7 Dual SSD RAID - [SOLVED] Installed Ubuntu on Pre- UEFI Win 
[http://ubuntuforums.org/showthread.php?t=2240043](http://ubuntuforums.org/showthread.php?t=2240043)
Acer Aspire S7 can't install Ubuntu - UltraBook erased RAID 0 meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)

Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator)
Acer Travelmate B117 (success - after some UEFI boot troubles) Trust related
[https://forum.siduction.org/index.php?topic=6272.0](https://forum.siduction.org/index.php?topic=6272.0)

---

### Post by xarctus on 2019-10-17
Thanks, I tried what you suggested but it did not help.

However, I was able to solve the problem based on this solution:  [18.04 and 18.10 fail to boot nvme0: failed to set APST feature (-19)]("https://askubuntu.com/questions/1099048/18-04-and-18-10-fail-to-boot-nvme0-failed-to-set-apst-feature-19")
  At boot in grub I select install ubuntu and I press e then escape and  I edit the boot option there so that after quiet splash I have  nvme_core.default_ps_max_latency_us=200
  This way I was able to see the SSD disk.

---

