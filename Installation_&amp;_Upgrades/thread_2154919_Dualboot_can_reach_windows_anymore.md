---
title: "Dualboot can reach windows anymore"
date: 2013-06-16
forum: Installation &amp; Upgrades
---

### Post by Phenics on 2013-06-16
Hi all,


I hope someone can help me with this problem of mine. 

I´ve got a Lenove y500 preinstalled with Windows 8. Installed Ubuntu 13 on it this weekend which went reasanbly smooth after some initial issues. Both are installed in UEFI mode. 

Current issue: I can´t start Windows up  (after a change, i think it was made by the Grub Customizer). 

What do I see: at startup the multiboot screen appears. Which looks ok to me. It contains several Windows and Ubuntu options. 
If I choose for one of the windows-options i get a message which contains something like: ¨Secure boot forbids loading module from (hd0,gpt9)/boot/grub/x86_64-efi/ntfs.mod...reading sector...failed.. no such device..can find drivemap, invalid EFI file path¨

I ran the boot-repair application which results in the next log: [http://paste.ubuntu.com/5771063/](http://paste.ubuntu.com/5771063/)

---

### Post by fantab on 2013-06-16
Did Boot-Repair fix your issue? what happens when you boot after running Boot Repair?

---

### Post by Phenics on 2013-06-16
> **fantab said:**
> Did Boot-Repair fix your issue? what happens when you boot after running Boot Repair?

No it did not. After runnning boot repair it gave me the above log and results. 

It did do something though. My menu looked a little bit different.

---

### Post by oldfred on 2013-06-16
It looks looks like Boot-Repair did the convert to signed kernel and renamed Windows boot file to allow the grub shim file that has  the Microsoft key to work with secure boot on.

The standard os-prober Windows entries will not work, but the new entries that Boot-Repair adds to 25_custom should boot Windows with secure boot on. Or if your system allows booting Windows with secure boot off.

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bkpbootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

Boot-Repair also has done this:

 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi

---

