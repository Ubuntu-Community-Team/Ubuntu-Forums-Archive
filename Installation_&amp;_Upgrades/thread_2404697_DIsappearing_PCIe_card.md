---
title: "DIsappearing PCIe card"
date: 2018-10-27
forum: Installation &amp; Upgrades
---

### Post by pshepherd on 2018-10-27
I have had an xubuntu 14.04 system running happily for 3+ years.  


The oher day I the machine from a USB stick and installed xubuntu 18.04.1 onto a separate partition of the SDD.  The install seemed to work ok although there was a problem updating the grub entry. I rebooted 14.04 and ran grub-repair which solved the problem.  So far so good.


I have a DVB-S2 PCIe card (TBS 6982SE) in the machine which was working just fine however if I now boot from either the 14.04 or the 18.04 partition it does not show up in boot log, it has disappeared.  I have tried the card in a different socket, checked the auxiliary power to the card, it is not visible in dmesg/syslog. 


I have put the card in a different PC running Windows, installed the drivers and it works. So the card appears to be fine and used to work in the 14.04 box (which has a 'legacy boot' ie not UEFI).


Does the 18.04 installer or boot process potentially do anything to the bios, mobo or other card firmware which could cause the TBS card to disappear?


TIA


paul

---

### Post by dino99 on 2018-10-27
Check that lshw find that device first; then glance at 'journalctl -b' to know about issues.

---

