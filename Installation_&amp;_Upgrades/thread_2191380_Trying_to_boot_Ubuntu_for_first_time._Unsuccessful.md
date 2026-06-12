---
title: "Trying to boot Ubuntu for first time. Unsuccessfully"
date: 2013-12-02
forum: Installation &amp; Upgrades
---

### Post by sdhoefelmann on 2013-12-02
I have a Gateway sx2110G uw23 that I am booting from a usb stick (ubuntu 12.04 64 bit amd). when it starts up I go to a boot menu and boot using uefi. Instead of loading a gui it shows an ubuntu logo with a tracking bar and then sits at a command prompt. Anyone with a similar experience?

---

### Post by Bucky Ball on 2013-12-02
*Thread moved to **Installation & Upgrades**.*

Welcome. When you get to the menu at the beginning of the install, hit F6 and choose 'nomodset'. Proceed. Any luck?

---

### Post by sdhoefelmann on 2013-12-02
it loads a menu that gives the options try without installing, install ubuntu, and check disk for errors. Is this the menu at the beginning you are referring to?

---

### Post by sdhoefelmann on 2013-12-02
after choosing install ubuntu it shows the ubuntu logo with the tracking bar for a bit and then I get prompt that shows:

BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4.1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)_

---

### Post by oldfred on 2013-12-02
Are you using the 64 bit version?

 Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by fantab on 2013-12-02
Boot your Ubuntu USB and "Try Ubuntu without installing", Open Terminal [ctrl + alt + T], run the following commands and post its output here:

```
sudo parted -l
sudo fdisk -l
```

---

