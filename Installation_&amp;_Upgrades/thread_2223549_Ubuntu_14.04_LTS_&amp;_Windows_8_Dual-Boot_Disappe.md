---
title: "Ubuntu 14.04 LTS &amp; Windows 8 Dual-Boot: Disappearing GRUB Menu"
date: 2014-05-11
forum: Installation &amp; Upgrades
---

### Post by akylasa09 on 2014-05-11
I installed Ubuntu 14.04 LTS on my Dell XPS 8500 dual-booted with Windows 8.  GPT/UEFI/Secure Boot Disabled.  I can turn the computer off and on as many times as I want as long as I only select Ubuntu on the GRUB Menu, and no problems will arise.  However, every time I select and boot into Windows 8, the GRUB Menu disappears on reboot and booting into Ubuntu becomes impossible until I run boot-repair using a live-USB.  If checking boot-order in BIOS, when the GRUB Menu exists, "Ubuntu" is the only option to boot.  Selecting this option leads to the GRUB Menu.  After Windows seemingly overrides it, "Windows Bootloader" is the only option.

I have read into this thread: [http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)

Checking off the [COLOR=#000000]Boot-Repair --> Adv options --> tick "Backup and rename EFI files"[/COLOR] does not change the results.  The GRUB Menu still disappears after I boot into Windows 8 and it is still impossible to boot into Ubuntu.

---

### Post by oldfred on 2014-05-11
Post link to BootInfo report from Boot-Repair.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

