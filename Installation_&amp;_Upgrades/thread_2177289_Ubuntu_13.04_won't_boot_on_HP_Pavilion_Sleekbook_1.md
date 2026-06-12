---
title: "Ubuntu 13.04 won't boot on HP Pavilion Sleekbook 15 - b135ea"
date: 2013-09-28
forum: Installation &amp; Upgrades
---

### Post by fergus2 on 2013-09-28
After much faffing (turns out you need to press Fn+F10 to get into the BIOS), I seem to have managed to install Ubuntu 13.04 on my laptop - I got it to boot from a stick I'd just formatted using the Universal USB Installer and Raring Ringtail. However, while there were no apparent problems with the installation process itself - I got that 'Installation Succeeded! You may now want to restart' message - it still boots straight into Windows every time. This is bad, because Windows 8 is a terrible terrible operating system. Anyway, backing up the impression that there is in fact a copy of Ubuntu installed on my hard drive, there's now a great big partition that Windows detects but won't read, and when I booted from the USB stick again, it asked if I wanted to reinstall, or wipe out the previous installation of Ubuntu 13.04. I tried reinstalling first, but got stuck with the partitioning bit, so then I went with the second option. Again it said I'd succeeded in installing, but then booted into Windows.

The BIOS gives two sets of boot options: you can switch on Legacy Support, for 'old operating systems, like Windows 7 or DOS', or the more modern one, UEFI, for Windows 8 and such. The latter includes 'OS boot loader' in the boot order thing, as well as USB, etc.; the former has 'Notebook hard drive'. I've tried with both, and still only get Windows 8 unless I put USB at the top and boot off the stick. That actually works with nary a hitch, but I don't really want to always be booting off a pen drive.

Any ideas? Googling has turned up lots of people having trouble installing Ubuntu on HP Pavilions, but nobody with this specific problem.

Thanks!

---

### Post by fergus2 on 2013-09-28
Ohh... after even more googling, I found the answer at [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported) - I needed to hold down Shift while telling Windows to restart, and tell it to boot from another device. How absurd! Anyway, problem solved. Hopefully this post will make it easier for someone else to fix the same thing next time...

---

### Post by oldfred on 2013-09-28
You should be able to go into UEFI and change boot order, if Ubuntu is also installed in UEFI mode.

If you installed Ubuntu in BIOS/CSM/Legacy mode, you can use Boot-Repair to convert to UEFI by uninstalling grub-pc(BIOS) and installing grub-efi(UEFI). You may need to run Boot-Repair anyway as grub2's os-prober has a bug and only creates BIOS entries for Windows that will not work with UEFI.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry from os-prober that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
os-prober fix in grub2_2.00-14 and os-prober_1.58 from Debian

---

