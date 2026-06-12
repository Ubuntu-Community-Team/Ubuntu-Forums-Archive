---
title: "Problems with Windows 8.1 Upgrade and GNU GRUB Minimal BASH screen"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by rosemarie2 on 2014-04-05
Hi, I upgraded to Windows 8.1 today and then my computer started to just automatically load into my Windows section instead of Ubuntu 12.04 (and no options screen at the beginning). So I went into Ubuntu and ran Boot Recovery but something must have not worked as now when I go into Ubuntu it just comes up with:

"GNU GRUB version 1.99-21ubuntu3.14

Minimal BASH-like line editing is supported, For he first word, TAB  lists possible command completions. Anywhere else TAB lists possible device or file completions."

I have all my files backed up so I was just going to re-install the Ubuntu 12.04, but I can't get the machine to boot from the USB even though I've turned off Secure Boot & Fast Boot.

I have no disc drive.

Thoughts/Ideas on what to do next?

To sum up problems:
- Ubuntu partition showing GNU GRUB....Minimal BASH....
- No options at start up to choose what system to boot into
- Not booting from a bootable USB

Thanks!!

---

### Post by oldfred on 2014-04-05
Your update probably overwrote UEFI with Windows as default, reset to secure boot and turned fastboot back on.
You neeed to undo the secure boot, turn off fastboot.
Only secure boot systems will boot with secure boot on.

Some have to fully reset system by removing battery and holding power switch for a few seconds to drain residual power.

Go back thru all the Windows & UEFI settings needed before an install.
 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

