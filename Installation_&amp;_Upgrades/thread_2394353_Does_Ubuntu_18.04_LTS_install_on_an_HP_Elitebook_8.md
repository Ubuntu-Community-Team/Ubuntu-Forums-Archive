---
title: "Does Ubuntu 18.04 LTS install on an HP Elitebook 840 G4?"
date: 2018-06-15
forum: Installation &amp; Upgrades
---

### Post by karen.pardos on 2018-06-15
Hi there,

I'm about to get a new laptop that I wish to install Ubuntu on. In particular I'm looking at the HP Elitebook series.

Only generation 2 (G2) of the HP Elitebooks are so far [listed as certified by Ubuntu]("https://certification.ubuntu.com/certification/make/HP/?query=elitebook&category=Laptop&release=&level=Any").

So I wanted to know if anyone has tried to install (with success) Ubuntu on an [HP Elitebook 840 G4]("http://www8.hp.com/us/en/products/laptops/product-detail.html?oid=11122291#!tab=specs")?

Thanks,
Karen

---

### Post by oldfred on 2018-06-16
Someone may have installed to your specific model.

But issues are more common by brand, and with in brand whether AMD or Intel. And then which video is used.

I have seen many installs to various HP models, but almost all have required some sort of work around. HP violates UEFI spec that says NOT to use description as part of boot. And of course only valid description is "Windows Boot Manager". Generally you cannot set 'ubuntu' as default boot but then can use HP's fallback/hard drive boot entry as default and make that actually boot Ubuntu. If no Windows we normally just use "Windows Boot Manager" as description but make UEFI entry actually boot Ubuntu/grub. 
Some newer HP seem to work better than the older ones. You should update UEFI and that may improve things also. Update of UEFI required for all systems, anyway.

       HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work
[https://ubuntuforums.org/showthread.php?t=2390309](https://ubuntuforums.org/showthread.php?t=2390309)
HP 11m reinstall Windows & dual boot with Ubuntu 16.04
[https://ubuntuforums.org/showthread.php?t=2389104](https://ubuntuforums.org/showthread.php?t=2389104)
Probook G4 470 Ubuntu works fine with UEFI and secure boot. 
[https://ubuntuforums.org/showthread.php?t=2381663](https://ubuntuforums.org/showthread.php?t=2381663) 
    
       HP - escape + F9 for boot menu, F10 for bios setup
[http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453](http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453)
[http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook) 
    
Boot-Repair now does to copy of shimx64.efi to the fallback boot entry of /EFI/Boot/bootx64.efi, so manual copy not now required if you run Boot-Repair.
       HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 
    
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

