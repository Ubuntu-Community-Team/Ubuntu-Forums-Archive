---
title: "Dual-boot completely failed, neither Windows nor Ubuntu boot"
date: 2017-01-16
forum: Installation &amp; Upgrades
---

### Post by murphdasurf on 2017-01-16
I simply tried to install Ubuntu as a dual-boot and during the installation process everything felt alright. When I restarted the computer, Windows started, no grub, no sign of Ubuntu. Then I checked and found some information about Boot-Repair which I executed with a backup of the Windows 10 file and it produced the following output: [http://paste2.org/eXd9W1bO](http://paste2.org/eXd9W1bO) - as in this configuration neither Linux nor Windows were booting, I tried it again: [http://paste2.org/KBZyvC08](http://paste2.org/KBZyvC08) - still no sign of improvement.

After the execution of Boot-Repair nothing wants to start anymore:
[ATTACH=CONFIG]273223[/ATTACH]

Just a Windows Boot Manager is available, I can not select hard drives or anything else.
[ATTACH=CONFIG]273224[/ATTACH]

Some information regarding the system.
[ATTACH=CONFIG]273225[/ATTACH]

I do not understand much about how booting works and the more I tried to understand what was going on the more I realized how complex the issue is. Is there a quick way out? I prefer a dual-boot system but if that is too difficult, I will use a virtual machine and stay with my Windows system.

---

### Post by oldfred on 2017-01-16
UEFI & BIOS are incompatible.
Or you can only boot from UEFI menu and once you start booting in one mode cannot switch.
Or best to have all systems in UEFI boot mode if Windows is UEFI.

You have Windows installed in UEFI boot mode on sda that is gpt partitioned.
But you have Ubuntu installed in BIOS boot mode on sdb that is MBR(msdos) partitioned. 
But also have UEFI boot thru sda's ESP - efi system partition.

Better to start over, make sure sdb is UEFI with gpt partitioning.
How you boot install media is then how it installs.

But either way, all Acer have a unique requirement of setting an  UEFI supervisory password and enabling "trust" on the ubuntu/grub .efi files in the ESP from with in UEFI. Some older threads mention downgrading UEFI, but newer ones say to update to newest.

 Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

