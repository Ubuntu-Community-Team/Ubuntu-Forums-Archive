---
title: "Linux / Windows 8 Grub Boot Trouble"
date: 2014-11-30
forum: MINT
---

### Post by john_smith21 on 2014-11-30
Hard drive 1: 250GB SSD running Linux Mint 17.1
Hard drive 2: 480GB SSD running Windows 8.1 Pro

From a live cd I've mounted my Linux partition and installed grub2 on the first hard drive. On reboot I'm greeted with grub2 with these options:> Linux Mint 17.1

Linux Mint 17.1 Recovery

Memtest

Windows 8 (loader) on /dev/sdb1


Choosing Windows 8 gives this error:
> error: no such device: *serial number*
error: hd1 cannot get C/H/S values
error: hd1 cannot get C/H/S values
Press any key to continue...

I can boot to Linux Mint without issue. I've run 'sudo update-grub' which does allow me to boot to Windows, however, this will sometimes work for 1 reboot only. During my troubleshooting I did install grub on the Windows SSD as well. How can I clear the boot loader from both drives and start over? I would like the Windows 8 option from grub to work every time.

---

### Post by grahammechanical on 2014-11-30
I understand that there are Windows utilities that will restore Windows boot loaders. But be careful it does not put a Windows boot loader onto both disks. I am certain that will happen.

I do not support Linux MInt. I will tell you this. When we have a machine with Windows 8 pre-installed we need to follow this advice.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by oldfred on 2014-12-01
Moved to other OS.

Best to see details. Post link to summary report.
With 2 drives do NOT run auto fix. That just installs grub to both drives and we do not want that.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Current version ppa now available.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

