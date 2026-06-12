---
title: "How can I make a portable Ubuntu 20.04 installation?"
date: 2020-08-15
forum: Installation &amp; Upgrades
---

### Post by ia148-461 on 2020-08-15
Hello I have a spare 256GB SSD and a hard drive caddy with Thunderbolt 2 and USB 3.2 connections on it. Is it possible for me to use my Ubuntu 20.04 Live USB stick and install Ubuntu onto my external drive instead of the internal disk (/dev/sda) my external drive comes up as /dev/sdd. The machine I am using is not dual booted and only runs Ubuntu 20.04. I do not want to change my bootloader on my machine, however the problem is after I install Ubuntu onto my external drive I can only boot to that drive, if I remove that drive my internal drive no longer boots. How can I make an installation on the external drive without editing my internal drive bootloader? I want Ubuntu on my external drive so I can take it between different computers and boot it just by going into the BIOS boot device and selecting it. What am I not doing correctly?

Cheers.

---

### Post by MoebusNet on 2020-08-15
You don't need a whole SSD, you can even use a USB Flash Drive.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by C.S.Cameron on 2020-08-16
You can do no wrong if you unplug your internal drive before installing to the external drive.
Make sure you boot the installer drive in the same mode, BIOS or UEFI that the internal drive boots in.
After the install plug the internal drive back in and set the external drive as first hard drive, then run "sudo update grub" This will add the internal drive to it's GRUB BOOT menu.
If you plan on running the external on multiple computers you might want to make it bootable in either BIOS or UEFI, See: [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

---

### Post by sudodus on 2020-08-16
> **C.S.Cameron said:**
> You can do no wrong if you unplug your internal drive before installing to the external drive.
Make sure you boot the installer drive in the same mode, BIOS or UEFI that the internal drive boots in.
After the install plug the internal drive back in and set the external drive as first hard drive, then run "sudo update grub" This will add the internal drive to it's GRUB BOOT menu.
If you plan on running the external on multiple computers you might want to make it bootable in either BIOS or UEFI, See: [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

+1

See also the following links (and links from them),

- [Boot Up with USB SSD](https://ubuntuforums.org/showthread.php?t=2447539)

- [Can I install Ubuntu in a USB stick and run it as my learning machine? Will it run as a normal Ubuntu without difference?](https://askubuntu.com/questions/1267370/can-i-install-ubuntu-in-a-usb-stick-and-run-it-as-my-learning-machine-will-it-r/1267376#1267376)

---

### Post by oldfred on 2020-08-16
If you have partitioned in advance to have an ESP on external drive, you can just copy /EFI/ubuntu & /EFI/Boot from internal drive to external drive. Full version of grub makes a copy as /EFI/Boot/bootx64.efi which is what UEFI uses to boot external drives. But full version also requires files from /EFI/ubuntu.

And on internal drive you can just edit /EFI/ubuntu/grub.cfg to have correct UUID for internal install. 
Check UUID in fstab on external. You want UUID for ESP mount to be external drive's ESP, so major updates go into correct partition.

I have had same issue and just created new line in grub's configfile with correct UUID & partition.
```
fred@Bionic-Z170N:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
#search.fs_uuid 8402fb15-78ce-440e-8c84-828ba6a20abe root hd1,gpt8 
search.fs_uuid c29fc361-ea05-420b-b919-850aeef65dd4 root hd0,gpt4 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

```

#To see UUID.
sudo blkid
#or
lsblk -f
#Edit grub with correct UUID
sudoedit /boot/efi/EFI/ubuntu/grub.cfg

---

