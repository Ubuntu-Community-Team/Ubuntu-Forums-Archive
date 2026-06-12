---
title: "Cannot select device for boot loader installation - 24.04."
date: 2024-08-24
forum: Installation &amp; Upgrades
---

### Post by coffee-enthusiast on 2024-08-24
I have a dual booted machine with Win10 and 20.04. My current boot partition is on /dev/nvme0n1p2 and my Ubuntu installation is on /dev/nvme0n1p6 which I've confirmed via. I've attached a picture of what I see in the installer. The option to select the boot loader device is greyed out despite me manually setting the mount point on nvme0n1p2 to /boot/efi. I've also confirmed via GParted that that partition has "boot" and "esp" flags. In the past, the old installer was able to detect the efi partition and I just had to set the mount point on /dev/nvme0n1p6 to "/" for the installation to work. I would appreciate some help and advice on how to proceed. This is my first time using the new installer so I'm a little lost. I have backed up all my data, but I would *really* like to avoid deleting all my partitions to install to an empty disk.

I found a similar thread but I was advised to start my own thread -> [https://ubuntuforums.org/showthread.php?t=2499221](https://ubuntuforums.org/showthread.php?t=2499221)

I've also attached a picture of what the partition table looks like in GParted.

Thanks in advance

---

### Post by yancek on 2024-08-24
>  my Ubuntu installation is on /dev/nvme0n1p7 which I've confirmed 

What??  The images you posted clearly show it is on partition 6 NOT 7 as 7 is swap.  Is that a typo on your part?

---

### Post by coffee-enthusiast on 2024-08-24
> **yancek said:**
> What??  The images you posted clearly show it is on partition 6 NOT 7 as 7 is swap.  Is that a typo on your part?

@yancek you're right, it's a typo, thanks. My question still remains,however. Why is the boot installation device greyed out and how can I fix that?

---

### Post by oldfred on 2024-08-24
It shows bitlocker. That locks up ESP & all NTFS partitions.
Also then is AHCI mode on in UEFI settings for drive.
Windows updates may reset Windows settings turning fast startup or bitlocker back on or also update UEFI which may reset to defaults. 

AHCI enable - May have to unlock bitlocker if used
[https://superuser.com/questions/1280141/switch-raid-to-ahci-without-reinstalling-windows-10](https://superuser.com/questions/1280141/switch-raid-to-ahci-without-reinstalling-windows-10)
[https://askubuntu.com/questions/1305270/bitlocker-is-blocking-ubuntu-20-04-installation-in-a-dual-boot-system-with-windo](https://askubuntu.com/questions/1305270/bitlocker-is-blocking-ubuntu-20-04-installation-in-a-dual-boot-system-with-windo)
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)
Dual boot with Bitlocker works
[https://askubuntu.com/questions/1135654/how-to-install-ubuntu-alongside-bitlocker-encrypted-windows10](https://askubuntu.com/questions/1135654/how-to-install-ubuntu-alongside-bitlocker-encrypted-windows10) & 
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-running-windows-and-bitlocker-turned-on/15338licen](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-running-windows-and-bitlocker-turned-on/15338licen)
Bitlocker & keys info (Full Volume Encryption Key, FVEK),  (Volume Master Key, VMK) which encrypts the FVEK, but keys to encrypt the VMK. 
[https://ubuntuforums.org/showthread.php?t=2456222&p=14013210#post14013210](https://ubuntuforums.org/showthread.php?t=2456222&p=14013210#post14013210)

---

### Post by coffee-enthusiast on 2024-08-24
> **oldfred said:**
> It shows bitlocker. That locks up ESP & all NTFS partitions.
Also then is AHCI mode on in UEFI settings for drive.
Windows updates may reset Windows settings turning fast startup or bitlocker back on or also update UEFI which may reset to defaults. 

AHCI enable - May have to unlock bitlocker if used
[https://superuser.com/questions/1280141/switch-raid-to-ahci-without-reinstalling-windows-10](https://superuser.com/questions/1280141/switch-raid-to-ahci-without-reinstalling-windows-10)
[https://askubuntu.com/questions/1305270/bitlocker-is-blocking-ubuntu-20-04-installation-in-a-dual-boot-system-with-windo](https://askubuntu.com/questions/1305270/bitlocker-is-blocking-ubuntu-20-04-installation-in-a-dual-boot-system-with-windo)
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)
Dual boot with Bitlocker works
[https://askubuntu.com/questions/1135654/how-to-install-ubuntu-alongside-bitlocker-encrypted-windows10](https://askubuntu.com/questions/1135654/how-to-install-ubuntu-alongside-bitlocker-encrypted-windows10) & 
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-running-windows-and-bitlocker-turned-on/15338licen](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-running-windows-and-bitlocker-turned-on/15338licen)
Bitlocker & keys info (Full Volume Encryption Key, FVEK),  (Volume Master Key, VMK) which encrypts the FVEK, but keys to encrypt the VMK. 
[https://ubuntuforums.org/showthread.php?t=2456222&p=14013210#post14013210](https://ubuntuforums.org/showthread.php?t=2456222&p=14013210#post14013210)

Thanks for the response. Yes, AHCI mode is on. I don't think my efi partition is encrypted by Bitlocker because I'm able to navigate into it via the terminal in Ubuntu and read the contents. The Ubuntu installer also doesn't show a lock in that row to the very left like it does for the Windows partition on nvme0n1p4. Other than fast startup, which other settings should I check?

---

### Post by oldfred on 2024-08-24
See Tea for One's suggestions:
[https://ubuntuforums.org/showthread.php?t=2482889&p=14126324#post14126324](https://ubuntuforums.org/showthread.php?t=2482889&p=14126324#post14126324)

And link in my signature below.

---

### Post by coffee-enthusiast on 2024-08-24
> **oldfred said:**
> See Tea for One's suggestions:
[https://ubuntuforums.org/showthread.php?t=2482889&p=14126324#post14126324](https://ubuntuforums.org/showthread.php?t=2482889&p=14126324#post14126324)

And link in my signature below.

Thanks for that link. It made me realize I was booting the live USB in legacy mode, and not UEFI mode which resulted in the installer not recognizing the EFI partition. Everything ran smoothly once I booted the USB into UEFI mode.

---

