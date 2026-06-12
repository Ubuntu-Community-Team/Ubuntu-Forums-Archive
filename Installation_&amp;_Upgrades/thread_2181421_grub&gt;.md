---
title: "grub&gt;"
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by jkgoose937 on 2013-10-17
I just installed ubuntu 13.10 on my Toshiba satellite s855d-s15120, and I have a 74mb efi partition, 75mb biosgrub partition, 30gb / partition, 8gb swap partition, and 712gb /home partition. boot loader is on /dev/sda1 efi.  after I install it dumps me to "grub>"

any suggestions?

---

### Post by oldfred on 2013-10-18
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Usually better to have a larger efi partition, but that may work. And a bios_grub partition only needs to be 1MB unformatted space. But you only need efi partition if booting in UEFI mode and bios_grub if booting in BIOS mode. But normally not both.

Ubuntu will boot in either mode from gpt partitioned drive. And how it installs is based on how you boot install media.

---

