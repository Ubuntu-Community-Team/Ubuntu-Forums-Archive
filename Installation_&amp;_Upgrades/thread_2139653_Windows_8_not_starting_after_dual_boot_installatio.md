---
title: "Windows 8 not starting after dual boot installation with UEFI"
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by fbecaria on 2013-04-27
Hi, 

I followed the steps here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
I run the boot repair but doesn't work. In case any one can help me, here is the link: [http://paste.ubuntu.com/5608745/](http://paste.ubuntu.com/5608745/)

I'm trying to install ubuntu 13.04 (64 bits) in a sony vaio sve machine.

Thanks

---

### Post by oldfred on 2013-04-27
Are you booting this entry?
 menuentry "Windows UEFI bkpbootmgfw.efi" {

Do you have secure boot on or off. Some only boot with it on and it looks like you have the signed grub version installed so both Windows & Ubuntu should boot with secure boot on.

And you have two similar entries as your system as a vendor recovery boot partition with efi files that is not the efi partition. UEFI only boots from efi partition.

In grub menu you can press e and confirm it has UUID D826-A7E2 which is your efi partition.

Boot-Repair has run the second time, which renames the Windows boot file to really be the grub shim file which has the Microsoft secure boot signing key. That is required as some systems violate the UEFI standard and make changes so that only the Windows efi file will boot. 

You have already done this which should be ok:

 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 


 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work. (But you get two sets, one that will work and the other from a recovery partition)
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---

