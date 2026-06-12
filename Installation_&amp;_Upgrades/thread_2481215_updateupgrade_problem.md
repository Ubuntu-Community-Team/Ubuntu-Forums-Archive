---
title: "update/upgrade problem"
date: 2022-11-22
forum: Installation &amp; Upgrades
---

### Post by coley9225 on 2022-11-22
Hello all. I again come to humbly ask for help. I do update/upgrade almost daily. A week or so ago, I noticed that the grub upgrades were being held back. A couple days ago, they were released and attempted to upgrade the grub. It is saying I need to run 'sudo dpkg --configure -a', which I did. Now I am unable to install any packages.

This is the output I got from sudo apt upgrade and sudo dpkg --configure -a.
```
charles:$:sudo apt upgrade[sudo] password for charles: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
charles:$:sudo dpkg --configure -a
Setting up grub-efi-amd64 (2.06-2ubuntu10) ...
Trying to migrate /boot/efi into esp config
Installing grub to /boot/efi.
Installing for x86_64-efi platform.
grub-install: warning: Cannot set EFI variable Boot0000.
grub-install: warning: efivarfs_set_variable: writing to fd 8 failed: Interrupted system call.
grub-install: warning: _efi_set_variable_mode: ops->set_variable() failed: Interrupted system call.
grub-install: error: failed to register the EFI boot entry: Interrupted system call.
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Sourcing file `/etc/default/grub.d/lubuntu-grub-theme.cfg'
Generating grub configuration file ...
Found theme: /usr/share/grub/themes/lubuntu-grub-theme/theme.txt
Found linux image: /boot/vmlinuz-5.15.0-53-generic
Found initrd image: /boot/initrd.img-5.15.0-53-generic
Found linux image: /boot/vmlinuz-5.15.0-52-generic
Found initrd image: /boot/initrd.img-5.15.0-52-generic
Found linux image: /boot/vmlinuz-5.15.0-50-generic
Found initrd image: /boot/initrd.img-5.15.0-50-generic
Found linux image: /boot/vmlinuz-5.15.0-48-generic
Found initrd image: /boot/initrd.img-5.15.0-48-generic
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
##### Hung at this point, I waited 20 minutes and ctrl+c to exit ######
^Cdpkg: error processing package grub-efi-amd64 (--configure):
 installed grub-efi-amd64 package post-installation script subprocess was interrupted                                                         
dpkg: dependency problems prevent configuration of grub-efi-amd64-signed:                                                                     
 grub-efi-amd64-signed depends on grub-efi-amd64 | grub-pc; however:   
  Package grub-efi-amd64 is not configured yet.                        
  Package grub-pc is not installed.                                    
                                                                       
dpkg: error processing package grub-efi-amd64-signed (--configure):    
 dependency problems - leaving unconfigured                            
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for initramfs-tools (0.140ubuntu13) ...
update-initramfs: Generating /boot/initrd.img-5.15.0-53-generic
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
Errors were encountered while processing:
 grub-efi-amd64
 grub-efi-amd64-signed
charles:$:

```

At first, I thought it was machine specific, installing a linux distro on my laptop is quite a process, however, I have same issue with my desktop, which has no efi, bios only.

The above output indicates that grub-pc is not installed, but after a fresh install on a new ssd(or hdd), The first thing I have to do, to get rid of error messages, is purge and reinstall the grub, using the following commands:
```
sudo apt purge grub grub-pc grub-commonsudo apt install grub-common grub-pc
sudo update-grub
```

At this point, the computer seems to run fine, including reboots, but I need to get this resolve to be able to do updates/upgrades, and install/remove apps.
If you need any additional info, please let me know and I'll get right back to you.

Any guidance on this would greatly appreciated.

---

