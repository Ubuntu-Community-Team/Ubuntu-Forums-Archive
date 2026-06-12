---
title: "UEFI install// Acer Aspire S13 // LVM"
date: 2017-06-04
forum: Installation &amp; Upgrades
---

### Post by MikeCyber on 2017-06-04
Hi
how to install 17.04 with UEFI? I've selected legacy, installed, selected uefi and selected in security the linux boot. But still ubuntu only boots in legacy mode.
What did I do wrong?

What about the lvm install option? Does this works with Windows 10 aside? snapshots sounds very good...is this stable or am I to run into problems? Still ext4?
Thanks

---

### Post by oldfred on 2017-06-04
I consider LVM more for Advanced users. It is a logical volume manager inside the standard physical partitions. And then you have to use LVM tools or something more to learn.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

Ubuntu's default install of LVM erases entire hard drive as one of advantages of LVM is using the entire drive. So if you have Windows you have to do a manual install of LVM to part of the hard drive. 
But if you want full drive encryption then you have to use LVM.

You have either UEFI or Legacy. 
And how you boot install media UEFI or Legacy/BIOS/CSM is then how it installs. And then you have to have system set to boot in that same mode UEFI or legacy to have it work. There actually is a third mode UEFI with Secure boot. So odds or randomly installing from flash drive & and having system in in same boot mode is one in three. (not actually as if you  have UEFI secure boot on & install in secure boot you can only boot in secure boot).

And if you have Windows, better to install Ubuntu in same boot mode as Windows boots.

See summary install instructions in link in my signature. And further info also there.
Then if specific questions we can help.

---

### Post by MikeCyber on 2017-06-05
Thanks. Managed to install in UEFI by setting the usb stick as trusted in security, install, then set the ubuntu hd boot as trusted.
LVM seems complicated aside Windows so I left this for some other day.

---

### Post by oldfred on 2017-06-05
Is your Acer one of those that needs you to set a UEFI password and then enable "trust" on the .efi boot files inside the ESP from within the UEFI?
Also make sure you have newest UEFI from Acer. Some posts said to downgrade, but newer ones said newest from Acer works.

       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 
            Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by MikeCyber on 2017-06-06
yes uefi secure boot.
I'm very happy with my new travel companion. Small but powerful to even run 3D apps like x-plane. I got it for only ~500.-
All works out of the box.

---

