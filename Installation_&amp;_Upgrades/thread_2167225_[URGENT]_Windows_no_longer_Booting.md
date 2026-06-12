---
title: "[URGENT] Windows no longer Booting"
date: 2013-08-12
forum: Installation &amp; Upgrades
---

### Post by patrick10 on 2013-08-12
I just recently decided to try out linux and so I installed Ubuntu alongside my Windows 7 install. However, the boot manager gives me an error when attempting to boot Windows. Something along the lines of "Incorrect boot path"

---

### Post by oldfred on 2013-08-12
We need to see details.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by patrick10 on 2013-08-13
[http://paste.ubuntu.com/5980772/](http://paste.ubuntu.com/5980772/)
There is the URL Boot Repair gave me. Is there any other information needed to try and fix this?

---

### Post by oldfred on 2013-08-13
Did you now try the new entries from Boot-Repair?

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---

### Post by patrick10 on 2013-08-13
Nevermind, Boot Repair seems to have solved my problem

---

