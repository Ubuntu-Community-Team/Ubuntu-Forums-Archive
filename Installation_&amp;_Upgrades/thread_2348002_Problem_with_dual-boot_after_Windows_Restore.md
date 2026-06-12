---
title: "Problem with dual-boot after Windows Restore"
date: 2016-12-30
forum: Installation &amp; Upgrades
---

### Post by davidmgilo1 on 2016-12-30
Hi,

I had to restore windows to a previous point in my computer (Aspire E5-571G) that had(has) a dual boot with windows 8.1 and ubuntu 16.04.

I have tried following the guide [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) but it still loads windows directly.

I have got the info of boot-repair here: [http://paste2.org/7v1BN0FE](http://paste2.org/7v1BN0FE) and I've disabled Fast start up and secure boot.

Could anyone check what I am doing wrong? Thanks!

---

### Post by oldfred on 2016-12-30
Did Ubuntu boot before?
Had you set a UEFI supervisory password and enabled 'trust' on the ubuntu/grub .efi files in the ESP - efi system partition?
Scripts shows no efi files in the ESP, sda2, but that may be script as UEFI shows lots of entries & grub says it reinstalled ok.
Have you updated UEFI to newest from Acer? Some older threads say to downgrade UEFI, but newer ones say very newest UEFI from Acer works.
       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 

You show a lot of UEFI duplicate entries. Either live installer or once booted, you may want to houseclean duplicates.
sudo efibootmgr -v
      
 The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
sudo efibootmgr -b XXXX -B
man efibootmgr

---

