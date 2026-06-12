---
title: "Dual boot Windows10-Ubuntu: can't boot to ubuntu after the installation"
date: 2016-07-27
forum: Installation &amp; Upgrades
---

### Post by gabrielbeauchemin on 2016-07-27
Hi everyone :),

In tried maybe 5-10 to install gnu/Linux distro on my new Aspire v 15 V3-575T-51Q8 (Acer). It only work one time with Linux mint and I installed it in Legacy, So I needed to switch to legacy in the bio to be able to boot it...I now choose to install Ubuntu instead of Linux Mint, because I have many problems with the driver and I think I will have better chance and support with the Ubuntu community.

So I install it using these guide Lines:[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

-I install on usb using liliUsb creator the last Ubuntu Mate 64 bits
-I disable fastboot but not SRT as I didn't find any clear tutorial explaining how to and if I need to.
-I didn't use a image only usb because I felt it was tricky for me (not sure if I would did it right)
-When I installed it, I choose to install over the last Ubuntu installation I already made. I put a cable to my computer to internet so I could install on update and install also third party.

So my computer after this can't boot to ubuntu, it directly boot to windows. No grub. How can i acces to it?

Thanks very  much, I tried hard alone before asking it here. Its important for me to have gnu/linux on my computer.

---

### Post by oldfred on 2016-07-27
With Acer you have to set a supervisor password in UEFI and then enable "trust" on the grub/ubuntu .efi files in the ESP - efi system partition.

Some older threads mention, downgrading UEFI, but then even newer ones say you must upgrade to newest UEFI from Acer.

These all are essentially the same, but some are offer a bit more explanation than others.

 Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
Boot Parameter required
[http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10](http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10)
Acer E3-112-C0MQ - Bay Trail Issue Boot Parameter required
[http://ubuntuforums.org/showthread.php?t=2326162](http://ubuntuforums.org/showthread.php?t=2326162)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

---

### Post by gabrielbeauchemin on 2016-07-28
Thanks mate I'll look and try that :)

---

### Post by gabrielbeauchemin on 2016-08-02
It worked!! Thank much. I just add the efi file in the device in the ''enable Trust'' option. Thanks again! I will open another thread for others problems I now have regarding missing drivers.

---

