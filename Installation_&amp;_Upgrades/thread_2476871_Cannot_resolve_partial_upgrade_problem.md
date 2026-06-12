---
title: "Cannot resolve partial upgrade problem"
date: 2022-07-10
forum: Installation &amp; Upgrades
---

### Post by iwaddo on 2022-07-10
Hi, any help resolving the below problem would be gratefully appreciated. The upgrade has got stuck\broken and advises **sudo apt-get install -f** but as you can see it is not working.

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-5.15.0-33 linux-headers-5.15.0-33-generic linux-image-5.15.0-33-generic linux-modules-5.15.0-33-generic
  linux-modules-extra-5.15.0-33-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED
  linux-image-5.13.0-39-generic
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
3 not fully installed or removed.
After this operation, 10.3 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 221263 files and directories currently installed.)
Removing linux-image-5.13.0-39-generic (5.13.0-39.44) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.13.0-39-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.13.0-39-generic (--remove):
 installed linux-image-5.13.0-39-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.13.0-39-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Impavidus on 2022-07-10
Which release of Ubuntu?

Which kernel-related packages are installed? And which are broken?```
dpkg --list "linux-*"
dpkg --list | grep -v '^rc\|^ii'
```

Any other complicating factors, like a separate /boot partition or an encrypted system?

---

### Post by ActionParsnip on 2022-07-10
Looks like you need libssl-dev
[https://packages.ubuntu.com/search?searchon=contents&keywords=libcrypto.so&mode=exactfilename&suite=jammy&arch=any](https://packages.ubuntu.com/search?searchon=contents&keywords=libcrypto.so&mode=exactfilename&suite=jammy&arch=any)
You may need to make a symlink to make the file exist

---

### Post by iwaddo on 2022-07-10
Hi

The full list of packages is in the attached, the broken ones are

dpkg --list | grep -v '^rc\|^ii'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                       Version                                 Architecture Description
+++-==========================================-=======================================-============-================================================================================
rH  linux-image-5.13.0-39-generic              5.13.0-39.44                            amd64        Signed kernel image generic
iF  linux-image-5.15.0-33-generic              5.15.0-33.34                            amd64        Signed kernel image generic
iF  linux-image-5.15.0-40-generic              5.15.0-40.43                            amd64        Signed kernel image generic

Other complications may be that the drive is partitioned, I am able to boot into Windows 10 or Ubuntu, Windows 10 is the default
.
I have also included the output from a sudo fdisk -l but no idea if it helps.

Thank you for very much for your help and support

Regards

---

### Post by Impavidus on 2022-07-10
> **ActionParsnip said:**
> Looks like you need libssl-dev
[https://packages.ubuntu.com/search?searchon=contents&keywords=libcrypto.so&mode=exactfilename&suite=jammy&arch=any](https://packages.ubuntu.com/search?searchon=contents&keywords=libcrypto.so&mode=exactfilename&suite=jammy&arch=any)
You may need to make a symlink to make the file exist
It looks like that. You may have to reinstall that package.

> **iwaddo said:**
> 
Other complications may be that the drive is partitioned, I am able to boot into Windows 10 or Ubuntu, Windows 10 is the default

It would be really strange if the drive were not partitioned. Theoreticaly, you can make a filesystem on an unpartitioned drive, but nobody does anymore (it was done on floppies). There's always at least one partition. One peculiar thing though, it appears that you dual boot Ubuntu and Windows 10 on an MBR partitioned hard drive, presumably on a legacy (not uefi) system. That's very uncommon and a bit fragile, but that's not the cause of your problem.

---

