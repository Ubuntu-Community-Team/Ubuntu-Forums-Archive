---
title: "No GRUB menu after installing Ubuntu Studio 18.04"
date: 2018-07-10
forum: Installation &amp; Upgrades
---

### Post by belsean21 on 2018-07-10
I'm having a GRUB issue with a new installation of Ubuntu Studio 18.04 along side existing Win10 installation on a Dell Inspiron 7570

On reboot I get the grub> prompt and no menu.

If I enter

grub> set root=(hd0,gpt8)
grub> configfile /boot/grub/grub.cfg

The menu appears and I can boot both Win10 & Ubuntu Studio in the normal fashion.

Running boot-repair or grub-update haven't solved the problem
[http://paste.ubuntu.com/p/C5PkWC94ng/](http://paste.ubuntu.com/p/C5PkWC94ng/)

Any advise on how to fix this would be appreciated

Thanks,
Sean.

---

### Post by powerjas on 2018-07-10
Try turning off network/internet during install that worked for me to get installed. You can enable it and then update the system after it's booted.

---

### Post by oldfred on 2018-07-10
What brand/model system?

See this bug on 18.10 which installs grub, not ubuntu entry into UEFI. But it should not be happening on 18.04. Maybe they fixed 18.10's grub, but used the incorrect version as update to 18.04?

Your UEFI boot entries from report shows a grub, but not an ubuntu entry.
sudo efibootmgr -f
       Boot0001* grub    HD(1,GPT,5dd9f4b6-7f53-4ccf-9bcf-f33bd9b153ac,0x800,0xfa000)/File(EFIgrubshimx64.efi) 

In your ESP - efi system partition your /dev/nvme0n1p1, do you have /EFI/ubuntu or only /EFI/grub?

Quick fix is to create/copy /EFI/grub to /EFI/ubuntu. You may just really need /EFI/ubuntu/grub.cfg file.
I have tried to install Ubuntu using different efi boot names, but something internally is hard coded to only use /EFI/ubuntu/grub.cfg. The version of grub.cfg in ESP is just a three line configfile to find the full grub.cfg and is similar to your manually typed lines, except it uses the grub search function to find partition.

 Ubuntu 18.10 Cosmic installed /EFI/grub
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1775743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1775743) 

Since now also 18.04 you may need to post new bug for UEFI grub on 18.04, give version of grub and refer to above bug on 18.10's grub.
[https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2)

My grub & kernel versions:
fred@bionic-z97:~$ grub-install -V
grub-install (GRUB) 2.02-2ubuntu8
fred@bionic-z97:~$ uname -a
Linux bionic-z97 4.15.0-24-generic #26-Ubuntu SMP Wed Jun 13 08:44:47 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

this should be the grub.cfg (with your UUID), but it needs to be in this folder, if booted:
fred@bionic-z97:~$ cat /boot/efi/EFI/ubuntu/grub.cfg
#search.fs_uuid 6ee4e5b7-cd2f-43f7-bf48-508980d29277 root hd1,gpt12
search.fs_uuid 8c92557f-cc60-438b-b1ea-ffea0adf0a1a root hd0,gpt7 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

---

### Post by belsean21 on 2018-07-10
The laptop is a Dell Inspiron 7570

Copying /boot/efi/EFI/grub/grub.cfg to /boot/efi/EFI/ubuntu/ has fixed the missing boot menu. 

Thank you oldfred.

Regards,
Sean.

---

