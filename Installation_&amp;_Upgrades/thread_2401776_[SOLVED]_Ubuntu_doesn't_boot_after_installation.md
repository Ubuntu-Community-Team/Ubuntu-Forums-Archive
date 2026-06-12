---
title: "[SOLVED] Ubuntu doesn't boot after installation"
date: 2018-09-22
forum: Installation &amp; Upgrades
---

### Post by giord94 on 2018-09-22
Hi, everyone. I've replaced my windows 10 installation with ubuntu 18.04 on my computer. The installation seemed to be fine but now when I start my computer there is a screen which says "no bootable device on this computer". I've tried to manage with partions and grub installations but anything seems to work! :(

Here are the informations from boot-repair, I hope someone can help me:

[http://paste.ubuntu.com/p/bj5nySjybg/](http://paste.ubuntu.com/p/bj5nySjybg/)

---

### Post by yancek on 2018-09-22
What hardware do you have, which manufacturer (HP, Dell, Toshiba, Acer??)
You an EFI install so is UEFI enabled in the BIOS?
Do you have an option to boot from EFI file in the BIOS?  If so select the option to boot the file suggested in boot repair:  
 
sda1/EFI/ubuntu/shimx64.efi file!

There should be a key listed on boot for several seconds immediately after starting the computer.  This varies with manufacturer so watch the bottom of your monitor when you boot.

---

### Post by oldfred on 2018-09-22
You show Acer graphics, so it must be an Acer. And you have unknow where it should say ubuntu in UEFI boot from efibootmgr -v.

All Acer have an unique requirement of setting "trust" on the .efi boot file(s) inside the ESP - efi system partition from within UEFI.
Many Acer also need UEFI udpates from Acer.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator) 
   Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
    
You show generic kernel & grub, not signed. But Boot-Repair did not offer to upgrade to signed versions? Not sure with Acer if once you set "trust", whether you can turn UEFI Secure Boot off and boot or need to keep it on, but update to signed versions of kernel. Shimx64.efi is the version of grub for UEFI Secure Boot.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator) 
   Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by giord94 on 2018-09-22
Thank you oldfred, I’ve followed the first link you gave me and now it works! The only question I have is that it takes some time to start, but I don’t know if it’s normal

---

### Post by oldfred on 2018-09-22
What is some time?
There are a wide variety of things that can slow boot.
What is boot time?
systemd-analyze
And just look at top few entries:
systemd-analyze blame

My system shows this, system is usable in 22 sec, but userspace should not take this long for me.
fred@bionic-z97:~$ systemd-analyze
Startup finished in 11.470s (firmware) + 4.899s (loader) + 2.842s (kernel) + 22.205s (userspace) = 41.418s
graphical.target reached after 22.188s in userspace

---

### Post by giord94 on 2018-09-23
Thank you oldfred, it seems to be the same for me so it’s normal

---

