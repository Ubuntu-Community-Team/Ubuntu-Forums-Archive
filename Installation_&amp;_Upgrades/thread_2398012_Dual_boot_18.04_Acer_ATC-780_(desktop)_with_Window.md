---
title: "Dual boot 18.04 Acer ATC-780 (desktop) with Windows 10 fails."
date: 2018-08-06
forum: Installation &amp; Upgrades
---

### Post by Harix on 2018-08-06
On Acer ATC-780 with 1T hd I installed Ubuntu 18.04 from a disk  image beside W10 in a 500GB partition. The installation went completely normal but when it rebooted after installation it  only boots into W10. The bios has ¨windows boot manager¨ as option.
What to do?

---

### Post by oldfred on 2018-08-06
Every Acer we have seen so far need you to set an UEFI password (do not lose that or erase later) and enable "trust" on the Ubuntu/grub .efi boot entries from with in UEFI.

You also need to make sure you have newest UEFI from Acer for your system.
Note that most systems reset to defaults with new UEFI. Some settings may be saved, with old BIOS all settings were lost. I keep a list and reset or confirm settings after updates.

Some users with Acer explain it a bit differently but all are essentially the same.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[URL="https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
      [/URL]
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 
    [URL="https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
      [/URL]
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
    [URL="https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

### Post by Harix on 2018-08-06
Thanks, that looks very complicated...too may stories.
I am trying to install Ubuntu on a friends PC and do not want to take any risk!
Which one is best to try?

---

### Post by oldfred on 2018-08-06
UEFI update is needed on just about all systems. Acer should have details on that.

The trust settings details are all the same, just slightly different explanations.
If not your system, after setting trust, remove UEFI password or your friend may not be able to get into UEFI to make changes.

---

### Post by Harix on 2018-08-06
Thanks a lot, I will give it a try tomorrow!

---

