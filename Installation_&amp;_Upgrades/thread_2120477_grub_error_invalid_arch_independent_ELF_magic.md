---
title: "grub error: invalid arch independent ELF magic"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by elektronaut on 2013-02-26
Hi,

I installed Zentyal 3.01, which is based on Ubuntu 12.04, from a USB stick. This is a single operating system istallation with LVM and encryption, no Windows partition. When I tried to boot the system, I didn't get to the login screen, only the message 
```
error: invalid arch independent ELF magic
grub rescue > 
```
showed up. I then downloaded Ubuntu-Secure-Remix to try the tool Boot-Repair, but it didn't help. Searching the forum I found [_this thread_]("http://ubuntuforums.org/showthread.php?t=1965810"). After booting the Live CD again (from a USB stick) I entered these commands: ```
sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda 
``` (/boot is on sda1). OK, after rebooting from hard disk I got to a Grub option screen allowing me to choose between normal or secure boot. When I choose normal boot, I get to the passphrase entry page (the disk is encrypted), but the mouse and keyboard don't work all of a sudden, so I can't enter anything. If I boot into secure mode, I also get to the point where the passphrase is needed, this time in text mode. But the keyboard here also doesn't work. 
It's strange, I never had any problems using my mouse and keyboard with this computer and a previous install of Zentyal (version 2.2). What's even more puzzling, is that now even before the disk is accessed the keyboard often doesn't work, so I'm having trouble to enter the BIOS (or UEFI or whatever) :confused:
As I had my first shot on this with the tool Boot-Repair, I also uploaded a Boot Info Summary before and after the unsuccessful repair. Here they are: [_Before_]("http://paste.ubuntu.com/5568131/") and [_after_]("http://paste.ubuntu.com/5568163/"). 

I hope somebody here can help.

---

### Post by elektronaut on 2013-02-27
OK, I finally got this solved. Contrary to my first impression, the tool Boot-Repair works. My problem now was with the unresponsive keyboard which wouldn't let me enter my passphrase. Solution was to use a PS2 keyboard, it seems for some reasons the USB drivers weren't loaded yet. I first did boot the rescue console and ran this command (not sure if it was necessary):
```
apt-get install --reinstall grub-efi-amd64
```
Afterwards I rebooted normally and everything works fine now. In order to enable discovery of the USB keyboard at passphrase prompt I added the usb modules in the module definition file for initramfs-tools. See here: [http://wiki.debian.org/Keyboard#How_to_enable_USB_keyboard_in_initramfs]("http://wiki.debian.org/Keyboard#How_to_enable_USB_keyboard_in_initramfs")

---

