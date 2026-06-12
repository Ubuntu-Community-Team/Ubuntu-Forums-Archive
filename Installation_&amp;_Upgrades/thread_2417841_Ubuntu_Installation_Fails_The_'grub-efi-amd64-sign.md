---
title: "Ubuntu Installation Fails: The 'grub-efi-amd64-signed' package failed to install int."
date: 2019-04-28
forum: Installation &amp; Upgrades
---

### Post by kiki8668 on 2019-04-28
I am trying to dual boot my laptop with Windows 10 and Ubuntu. My laptop and Windows 10 is in UEFI mode. 
I get this error when trying to install: > The ' grub-efi-amd64-signed' package failed to install into / target/. Without the GRUB boot loader, the installed system will not boot.
I have disabled Secure Boot and Fast Boot and Fast Startup. I made sure the USB was GPT so it would be the same as the GPT SSD. 
I have also tried installing Ubuntu without bootloader by: ```
ubiquity -b
```
and installing a grub bootloader manually to a /boot partition with grub-install.
But that did not work and tried Ubuntu boot-repair and still does not work.
boot-repair log: [http://paste.ubuntu.com/p/CcKXqN5tJY/](http://paste.ubuntu.com/p/CcKXqN5tJY/)
This log will show you my partitions setup and etc.
And I tried to install grub efi to the EFI System Partition (Same EFI partition Windows uses) manually instead, but get an error: ```
Could not prepare Boot variable: No such file or directory 
grub-install: error: efibootmgr failed to register the boot entry: Input/output error.
```

Ubuntu shows up in the UEFI boot order, but whenever I try booting to ubuntu with uefi boot order, I get: > GRUB Minimal BASH-like line editing is supported
When using rEFInd to boot Ubuntu straight from the kernel, the error is > No init found. Try passing init= bootarg
I tried CHKDSK on the EFI System Partition to see if it was corrupt, but it was fine.
However, on ubuntu live usb, the output of efibootmgr is: > No BootOrder is set; firmware will attempt recovery

I have been working on this for a full day non-stop with 100 tabs open on Ubuntu Forums/stack exchange.

Much Help Appreciated!

---

### Post by oldfred on 2019-04-28
While you can have multiple FAT32 partitions, almost all systems only allow one ESP - efi system partition. So remove boot/esp flags from sdb4. It also is shown as ext4 which would not be correct for an ESP anyway. With UEFI/gpt only ESP gets boot flag.

Also Ubuntu's grub only wants to install to an ESP on the first drive. Unusually sda or first NVMe drive. When I installed another system just to see how grub works, it installed without issue to sdb. And when I install specifing sdb, I see a quick message where it says grub installing to sdb with --force, but it installs to sda.
I think Boot-Repair will with advanced options and full reinstall of UEFI version of grub install to sdb's ESP (if you only have one).
But you always install grub to a drive like sda or sdb, not a partition like sdb2 or sdb4. With UEFI, it knows that boot loader files will go into the ESP.

Ignore errors on sdb2. That is the Microsoft reserved and is required to be unformatted. Parted/gparted always flag as an error since unformatted, so Boot-Repair picks up that error.

Standard desktop installs do not need a /boot partition. And new versions of Ubuntu now use a swap file, so swap partition not required. If swap partition found, it will use it. You only need /(root), but often better to separate system from data or have separate /home or separate data partition(s).  I keep /home inside / in my SSD but have very large data partition on HDD.

The other thing you might consider is swapping drives. Drive order is normally seen by UEFI/BIOS as SATA port order. So you could move boot drive to SATA0 and have your current sda data drive in higher numbered SATA port.

---

### Post by kiki8668 on 2019-04-29
I have removed the second ESP and now only have one. I tried selecting sdb to install the bootloader and still gives the error:> The ' grub-efi-amd64-signed' package failed to install into / target/. Without the GRUB boot loader, the installed system will not boot.
I have removed the /boot partition and swap partition.
I cannot swap drives as the ssd I am using is a M.2 one.
Midway through the steps of boot-repair, when doing this command: > sudo chroot "/mnt/boot-sav/sdb6" dpkg --configure -a
I get this error: > Could not prepare Boot variable: No such file or directory
grub-install: error: efibootmgr failed to register the boot entry: Input/output error.

---

### Post by oldfred on 2019-04-29
Will Boot-Repair's advanced mode let you install to ESP on sdb?

If not add an ESP on sda.

---

### Post by Dennis N on 2019-04-29
Comments:

Looking at your /etc/fstab, line #476: this line apparently (based on mount point) is intended to mount your EFI system partition:
```
UUID=d416be3e-d1f1-4fc0-b831-a7f8f4f56776	/boot/efi	ext4	defaults	0	1
```
But this is wrong UUID and file system type for an EFI system partition, so it's not going to work. Not sure if you've made changes after generating this report, but in case you haven't this needed fixing. 

Also, #235 (grub.cfg) points to partition 4, but Ubuntu is on 6; and the UUID there matches nothing. Needs fixing.

---

### Post by kiki8668 on 2019-05-05
When using boot-repair, I still see the error that efibootmgr could not find boot order.
I tried installing the boot loader on sdb and sda and still does not work.
On sda I created an efi system partition and still does not work.

---

