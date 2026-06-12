---
title: "My system cannot boot.(Failed to open \EFI\BOOT\mmx64.efi -Not found......)"
date: 2019-01-12
forum: Installation &amp; Upgrades
---

### Post by iPhilip on 2019-01-12
The following is the error message when i am booting my computer.
============================================
Failed to open \EFI\BOOT\mmx64.efi -Not Found
Failed to load image \EFI\BOOT\mmx64.efi -Not Found
Failed to start MokManage: Not Found
Something has gone serious wrong:import_mok_state() failed
============================================

Before this,I has run some command to make the vmware workstation can run vm's.
these commnad lines are in lines:
  ```
137  cp vmmon.ko /lib/modules/4.15.0-20-generic/misc/vmmon.ko
  138  sudo cp vmmon.ko /lib/modules/4.15.0-20-generic/misc/vmmon.ko
  139  modprobe vmmon
  140  sudo modprobe vmmon
  141  openssl req -new -x509 -newkey rsa:2048 -keyout MOK.priv -outform DER -out MOK.der -nodes -days 36500 -subj "/CN=VMware/"
  142  sudo /usr/src/linux-headers-`uname -r`/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n vmmon)
  143  sudo /usr/src/linux-headers-`uname -r`/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n vmnet)
  144  sudo /usr/src/linux-headers-`uname -r`/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n vmnet
  145  uname -r
  146  mokutil --import MOK.der
  147  openssl req -new -x509 -newkey rsa:2048 -keyout MOK.priv -outform DER -out MOK.der -nodes -days 36500 -subj "/CN=VMware/"
  148  sudo /usr/src/linux-headers-`uname -r`/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n vmmon)
  149  sudo /usr/src/linux-headers-`uname -r`/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n vmnet)
  150  sudo mokutil --import MOK.der
  151  sudo update-grub
  152  history 
  153  sudo mount -t ntfs /dev/sda6 /media/philip/sda6
  154  modprobe vmmon
  155  sudo modprobe vmmon
  156  cd /boot/grub/
```

---

### Post by wildmanne39 on 2019-01-12
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by oldfred on 2019-01-12
Several others have had similar error.
The mmx64.efi is the key manager. Canonical cannot certify third party drivers, but a user can.
It used to be that you just turned off UEFI Secure boot. But Some want Secure Boot and proprietary drivers, so they have created a way for you to self certify (if from a source you trust).
The fix seems to be to copy mmx64.efi, if you have it, or copy grubx64.efi or any other boot file and rename it to mmx64.efi as temporary fix. Full install will have that file.

       System fails to boot with \EFI\BOOT\mmx64.efi - Not Found
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171)

---

### Post by iPhilip on 2019-01-13
Thank oldfred

i copied the file \EFI\ubuntu\mmx64.efi to directory \EFI\BOOT\

and my computer can boot!

---

### Post by oldfred on 2019-01-13
Glad that worked, you can change to [Solved].

---

