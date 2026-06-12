---
title: "Installing on Acer Aspire Switch 11"
date: 2018-04-30
forum: Installation &amp; Upgrades
---

### Post by stevie1943 on 2018-04-30
I am trying to install Ubuntu on my Acer Aspire Switch 11 which came with Windows 8.1 pre-installed.
It has one USB port, no DVD/cd drive, so I am using an external drive on the USB port.
There is 18.2GB of HDD free space.I have disabled fast start up and changed the boot order in UEFI to use USB CDROM.
Secure boot is disabled. In security options , FTPM is disabled.
On start up I get the options of Windows or Ubuntu. Trying to boot Ubuntu gives the message "Windows failed to start because a file is missing, missing file is : \ubuntu\winboot\wubildr.mbr   staus 0x000000f."
The CDROM starts but does not load Ubuntu.
I have tried a genuine Ubuntu DVD, genuine Ubuntu flash drive and a downloaded ISO from Canonical.
Files on the disc show WUBI is there and there is an option to use a CD boot helper which I have used, but still no luck.

Regards Steve

---

### Post by oldfred on 2018-04-30
Wubi does not work with gpt or then with UEFI.
Last supported version of wubi was 12.04.
       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)
[https://bugs.launchpad.net/wubi/+bug/1478239](https://bugs.launchpad.net/wubi/+bug/1478239)
But unoffical version here by hakuna_matata:
[https://github.com/hakuna-m/wubiuefi/wiki](https://github.com/hakuna-m/wubiuefi/wiki)

Acer often requires UEFI update & "trust" settings for UEFI install.

 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 

 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003) 

[URL="https://github.com/hakuna-m/wubiuefi/wiki"]
[/URL]

---

### Post by stevie1943 on 2018-04-30
Thanks to those who replied. It seems that I am unable to install Ubuntu in the way I was trying, so how do I go about installing Ubuntu on my machine, or am I stuck with Windows 8.1?

---

### Post by oldfred on 2018-04-30
Do not know how similar these are.
 Acer Swift 3
[https://ubuntuforums.org/showthread.php?t=2370998](https://ubuntuforums.org/showthread.php?t=2370998) 
      
 Acer Spin 5 Ubuntu 17.04 Needs Acer password & trust
[https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238](https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238) 
            Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

---

