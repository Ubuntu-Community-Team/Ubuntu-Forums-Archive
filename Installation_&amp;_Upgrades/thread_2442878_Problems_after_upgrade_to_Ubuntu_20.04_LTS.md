---
title: "Problems after upgrade to Ubuntu 20.04 LTS"
date: 2020-05-08
forum: Installation &amp; Upgrades
---

### Post by claudiovito-giacalone on 2020-05-08
Good morning to all of you,

My name is Claudio Claudio and yesterday I upgraded my laptop (Acer Aspire 5 AMD 64 bit processor) from Ubuntu 19.10 to Ubuntu 20.04  LTS.
Unfortunately during the update many error messages appear on my display but in the end the upgrade finish and on my laptop now I have Ubuntu 20.04 installed even if:

1- Ubuntu Software Center completely disappear (not in the dock not in the programs anymore). I have tried to install it from the terminal but without any luck
2- the Software Updater do not work anymore, it start the process but then stop it without any feedaback.
3- Synaptic tells there is a file to remove but after starting the process this message appear on my screen:
"E: linux-image-5.3.0-46-generic: installed linux-image-5.3.0-46-generic  package post-removal script subprocess returned error exit status 1"
 This is the total report:
```
(Reading database ... 191747 files and directories currently installed.) Removing linux-image-5.3.0-46-generic (5.3.0-46.38) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.3.0-46-generic
/etc/kernel/postrm.d/zz-update-grub:
/usr/sbin/grub-probe: error: failed to get canonical path of `rpool/ROOT/ubuntu_6tql39'.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.3.0-46-generic (--remove):
 installed linux-image-5.3.0-46-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.3.0-46-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up memtest86+ (5.01-3.1ubuntu1) ...
/usr/sbin/grub-probe: error: failed to get canonical path of `rpool/ROOT/ubuntu_6tql39'.
dpkg: error processing package memtest86+ (--configure):
 installed memtest86+ package post-installation script subprocess returned error exit status 1
Setting up linux-image-5.4.0-29-generic (5.4.0-29.33) ...
Setting up grub-pc (2.04-1ubuntu26) ...
/usr/sbin/grub-probe: error: failed to get canonical path of `rpool/ROOT/ubuntu_6tql39'.
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of grub-efi-amd64-signed:
 grub-efi-amd64-signed depends on grub-efi-amd64 | grub-pc; however:
  Package grub-efi-amd64 is not installed.
  Package grub-pc is not configured yet.

dpkg: error processing package grub-efi-amd64-signed (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed | grub-efi-arm64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.
  Package grub-efi-arm64-signed is not installed.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
Processing triggers for linux-image-5.4.0-29-generic (5.4.0-29.33) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-29-generic
W: Possible missing firmware /lib/firmware/amdgpu/navi12_vcn.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/arcturus_vcn.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi12_smc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/arcturus_smc.bin for module amdgpu
I: The initramfs will attempt to resume from /dev/sda3
I: (UUID=c0bdb73c-5d62-4d54-a2b7-c9c9595d29c5)
I: Set the RESUME variable to override this.
/etc/kernel/postinst.d/zz-update-grub:
/usr/sbin/grub-probe: error: failed to get canonical path of `rpool/ROOT/ubuntu_6tql39'.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.4.0-29-generic (--configure):
 installed linux-image-5.4.0-29-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 memtest86+
 grub-pc
 grub-efi-amd64-signed
 shim-signed
 linux-image-5.4.0-29-generic
```

More over I have tried to use the following command from the terminal:

```
sudo apt update && sudo apt dist-upgrade

Hit:1 http://archive.canonical.com/ubuntu eoan InRelease
Get:2 http://ubuntu.bhs.mirrors.ovh.net/ubuntu focal InRelease [265 kB]
Get:3 http://ubuntu.bhs.mirrors.ovh.net/ubuntu focal-updates InRelease [107 kB]
Get:4 http://ubuntu.bhs.mirrors.ovh.net/ubuntu focal-backports InRelease [98,3 kB]
Get:5 http://ubuntu.bhs.mirrors.ovh.net/ubuntu focal-security InRelease [107 kB]
Fetched 577 kB in 1s (435 kB/s)    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-5.3.0-46-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 11,4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 191747 files and directories currently installed.)
Removing linux-image-5.3.0-46-generic (5.3.0-46.38) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.3.0-46-generic
/etc/kernel/postrm.d/zz-update-grub:
/usr/sbin/grub-probe: error: failed to get canonical path of `rpool/ROOT/ubuntu_
6tql39'.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.3.0-46-generic (--remove):
 installed linux-image-5.3.0-46-generic package post-removal script subprocess r
eturned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.3.0-46-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

I hope you can support me on that. 
thank you very much in advance

---

