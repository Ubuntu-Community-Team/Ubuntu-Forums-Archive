---
title: "Problem with boot"
date: 2020-03-09
forum: Installation &amp; Upgrades
---

### Post by Kalamaius on 2020-03-09
Hello everyone. I have a problem with boot. First I've installed Windows 10 and after win I've installed primeos, an android-based os. On boot now with Gnu Grub I can choose Primeos or Windows. After I've installed ubuntu 19.10 alongside windows 10. Now on ubutu boot Grub2 I can only choose ubuntu or windows, there's no primeos entry. On ubuntu I've done ```
*sudo update*-*grub* 
``` but primeos doesn't appear. 
```
$ sudo update-grub
[sudo] password di chris: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.3.0-40-generic
Found initrd image: /boot/initrd.img-5.3.0-40-generic
Found linux image: /boot/vmlinuz-5.3.0-18-generic
Found initrd image: /boot/initrd.img-5.3.0-18-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done


```
To get Primeos working I have to entry bios boot choice and put primeos as first. But in this way I get on boot gnu grub with primeos and windows, no ubuntu entry. 
This is efibootmgr output:
```
efibootmgr
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0002,0000,0003,0001,0006,0007,0004,0005,0008
Boot0000* Windows Boot Manager
Boot0001* PrimeOS
Boot0002* ubuntu
Boot0003* ubuntu
Boot0004* UEFI:CD/DVD Drive
Boot0005* UEFI:Removable Device
Boot0006* Prime OS Loader
Boot0007* ubuntu
Boot0008* UEFI:Network Device

```
What can i do to see primeos entry on ubuntu grub2?

---

### Post by yancek on 2020-03-09
If PrimeOS is similar to Android, it uses a basic Linux kernel (probably modified) and a very modified version of Grub2.  On Android, if I open a terminal as root and run:  ls /  it shows a completely different output than one sees on a standard Linux systems such as Ubuntu.  Android has an android.cfg file on the efi partition which is similar to grub.cfg (/efi/boot/android.cfg).  I expect that the reason grub2 on Ubuntu doesn't find PrimeOS is because of the non-standard location of the kernel.  You will likely need to manually create a menuentry for PrimeOS to put it the Ubuntu grub.cfg file.  If PrimeOS uses the same file (android.cfg) it should be located in /efi/boot.  You will need to look for it on the system and then copy and modify it to work in the Ubuntu Grub becasue the menuentries in Android are not like those in regular Grub.  I expect you will need to mount the PrimeOS partition and/or the efi partition with the PrimeOS files and do this from Ubuntu.

Some very basic Linux commands which do not work at all on Android:  grub-mkconfig, fdisk, gdisk, parted.

 If you don't get this working, you might try a new thread with a more appropriate title indicating you are trying to boot an Android type system.

---

