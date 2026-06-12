---
title: "Having difficulties installing Ubuntu 20.04 alongside Windows 8.1 (GRUB)"
date: 2020-10-01
forum: Installation &amp; Upgrades
---

### Post by grailswebdev on 2020-10-01
I'd like to install Ubuntu 20.04 on the same drive where my Win8.1. For Ubuntu I want a full disk encryption with Luks/LVM. **Additionally I want to install the Ubuntu boot loader (kernels/grub menu) on an external USB stick.** The goal is to boot Windows normally without the USB stick present but when I plug in the USB drive it should boot Ubuntu 20.04 instead. Does anyone tell me how to archive this? This is what I tried but it failed to boot properly and I ended up in a Grub prompt (Minimal Bash-like line editing is supported...)   
 
 1. I started Ubuntu with the Live-CD
 2. I created the disk encryption with cryptsetup
 
 
 [PHP]
cryptsetup luksFormat /dev/sda6
cryptsetup luksOpen /dev/sda6 box
pvcreate /dev/mapper/box
vgcreate cryptbox /dev/mapper/box
lvcreate -n root -L 30g cryptbox
lvcreate -n home -l 100%FREE cryptbox
[/PHP] 

3. Then I ran the "Install Ubuntu 20.04" ubiquity installer
 4. I choose "Normal installation" without Internet connection and "Install third-party software for graphics and Wi-Fi hardware..."
 5. On screen "Installation Type" I choose "Something else" to get into the partioning dialog.
 6. There I mapped /dev/mapper/cryptbox-root to / and /dev/cryptbox-home to /home
 7. For "Device for boot loader installation:" I picked my external USB stick which is on /dev/sdc1
 8. On "Installation Complete" I clicked "Continue Testing" to return to the terminal once again
 9.  
 
 [PHP]
blkid /dev/sda6 (needed for crypttab later on)

mount /dev/mapper/cryptbox-root /mnt
mount /dev/mapper/cryptbox-home /mnt/home
mount /dev/sdc1 /mnt/boot
chroot /mnt
mount -t proc proc /proc
mount -t sysfs sys /sys
mount -t devpts devpts /dev/pts
nano /etc/crypttab
 
box UUID=<from blkid on sda6> none luks
[/PHP] 
 
 10. Then
[PHP]update-initramfs -k all -c[/PHP]

 (Here I didn't see any useful output)
 
 
 11. Exit terminal and reboot
 
 But I only into a Grub> prompt. Can anyone help where I went wrong? I want the start-up kernel(s) on my external USB drive only root and home directories on my normal hard drive. BTW, did I miss /boot somewhere? I thought the installer is taking care of it.  
 
 Any hints and help is greatly appreciated.

---

### Post by oldfred on 2020-10-01
You should not need /boot on USB flash drive, but if UEFI system, you need an ESP - efi system partition, FAT32 with boot/esp flags. Windows uses 100MB, but Linux suggests 300 to 500MB but more for future use or multiple installs, or systemD-boot which puts most of /boot into ESP.

Ubuntu's Ubiquity installer only installs grub to ESP on first drive, usually the ESP that you have for Windows. You probably have to manually reinstall grub either command line or with Boot-Repair and remove the /EFI/ubuntu folder in the ESP on internal drive and remove the UEFI boot entry that boots from the Windows ESP. 

External drives only UEFI boot from /EFI/Boot/bootx64.efi which is what was used to boot live installer. But full install of grub to external drive needs both /EFI/Boot and /EFI/ubuntu to have the additional grub files.

Be sure to mount & decrypt your encrypted volumes, so Boot-Repair can correctly see your system. Its advanced mode can let you install grub to another drive if ESP exists on that drive.
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by watchpocket on 2020-10-01
> **grailswebdev said:**
> 4. I choose "Normal installation" without Internet connection and "Install third-party software for graphics and Wi-Fi hardware..."

Remember that the only way you can install third-party software during  the install process is by downloading it.  You can't do that if you have no internet connectivity. It's downloaded automatically by  the installer, but only if you're connected.

---

