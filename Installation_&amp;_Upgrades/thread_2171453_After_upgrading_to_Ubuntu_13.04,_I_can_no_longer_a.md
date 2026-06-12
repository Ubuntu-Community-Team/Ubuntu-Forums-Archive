---
title: "After upgrading to Ubuntu 13.04, I can no longer access Windows 7"
date: 2013-08-30
forum: Installation &amp; Upgrades
---

### Post by BlackL1ght on 2013-08-30
As in the title, I can no longer access windows 7. The boot menu option I used to use to boot Windows 7 now says "Invalid EFI file path". I upgraded using the 13.04 iso burned to a CD. 

When I run boot-repair, it fails. Here is the report it gives: [http://paste.ubuntu.com/6045165/](http://paste.ubuntu.com/6045165/)

Any ideas?

---

### Post by varunendra on 2013-08-31
It seems you have installed 32 bit version of Ubuntu 13.04.

For EFI support, you must install 64 bit version. Please see : [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and try reinstalling 64 bit instead, on the same partition, overwriting the current installation.

If a fresh installation is a problem, please post back the reason why you want to save the current installation, or what you want to save in it, and maybe we can figure out a way for you.

---

### Post by oldfred on 2013-08-31
You say you are installing 13.04, but your CD is this?
>  /dev/sr0                                                iso9660    Xubuntu 11.10 amd64



With UEFI best to use most current version as UEFI has lots of fixes with each new version. And as varunendra says you must use the 64 bit version. More info on UEFI installs in link in my signature. Best to set UEFI/BIOS to boot in UEFI mode only if you can, so you do not boot in CSM/BIOS mode.

---

