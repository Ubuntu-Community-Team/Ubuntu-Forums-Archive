---
title: "Installation failed - grub problem"
date: 2018-02-23
forum: Installation &amp; Upgrades
---

### Post by panditax on 2018-02-23
Greetings,

I'm trying to install Ubuntu in the following config:
- UEFI enabled, secure boot disabled,
- LUKS encrypted LVM partition

and it fails on grub-install, with  '*grub*-*efi*-*amd64*-*signed*' package *failed to install into* /*target*/' error, then insaller crashes.

Some details:
- SSD 
- /dev/sda1 as EFI System partition type (1GB)
- /dev/sda2 as Linux LVM type (375GB)

I can't make this config in Ubuntu installer, because it doesn't allow to change the config. It uses 100% SSD, and makes "root" nearly 100% of LVM. It is not what I need. It's pretty funny that installer doesn't allow any changes.
So I begin with partitioning with gdisk, formating /dev/sda1 to fat32, then luksFormat of sda2, then creating lvs. Next I run installer, choose to use "something else" when it comes to partitioning. There I set to format /, swap and home, and specify /dev/sda as a device for boot loader instalation.

I saw a lot of similar problems but couldn't find and solution which would have worked in my case. I tried to install grub by hand, using ubuntu and grml live. I dropped this idea as it is more complicated and makes many more problems to solve.

Simple system installation became a nightmare. Please help me. I would be grateful for any input.

Regards

---

### Post by oldfred on 2018-02-24
HP is not particularly friendly to dual boot or Linux installs. It violates UEFI standard that says not to use description as part of UEFI boot. And only valid description is "Windows Boot Manger". But various work arounds depending on configuration.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

See link in my signature and these threads.
If only booting Ubuntu, you may need to manually add a new UEFI entry with efibootmgr  with description "Windows Boot Manager" but actually using shimx64.efi as boot file. 


 Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others workarounds:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)

---

