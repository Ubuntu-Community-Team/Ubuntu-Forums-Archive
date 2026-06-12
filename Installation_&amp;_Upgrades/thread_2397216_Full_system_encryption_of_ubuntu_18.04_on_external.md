---
title: "Full system encryption of ubuntu 18.04 on external HDD"
date: 2018-07-26
forum: Installation &amp; Upgrades
---

### Post by iason.manolas on 2018-07-26
Hello, after installing ubuntu unencrypted on an external drive, I am now trying to do a full system encryption installation of ubuntu on an external hdd drive, For doing that I used the instructions of [this]("https://help.ubuntu.com/community/ManualFullSystemEncryption") site. After I finish the installation and try to boot into the external drive I end up in the grub terminal. Since the situation is quite complicated I was unable to find previous attempts and issues. For the unencrypted installation I used [this]("https://www.dionysopoulos.me/253-portable-ubuntu-on-usb-hdd.html") tutorial. I believe I need to combine the two sites and specifically I need to use the following command (see the end of the second link):
```
grub-install -d /usr/lib/grub/x86_64-efi --efi-directory=/boot/efi/ --removable ***/dev/sdX***
```

I am quite confused on what I need to do to make this happen.. Any ideas?****

---

### Post by oldfred on 2018-07-26
Is system UEFI or BIOS?
Do you have an ESP - efi system partition on first drive, usually sda?
Did Ubuntu install its UEFI grub boot files into ESP on sda?

I normally just copy all the /EFI/ubuntu folder twice from internal ESP  to external drive's ESP. Once to /EFI/ubuntu and once to /EFI/Boot and rename shimx64.efi to bootx64.efi. External drives in UEFI mode only boot from /EFI/Boot/bootx64.efi and shimx64.efi is internally expecting to find more files in /EFI/ubuntu.

But now grub does install files to /EFI/Boot. Have not yet experimented to see it that works on its own or needs other files also.

---

### Post by iason.manolas on 2018-07-27
My system is uefi.
yes.
No on sdb which is my external drive. I did that so my ubuntu os is portable.

---

### Post by oldfred on 2018-07-27
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by C.S.Cameron on 2018-07-27
I have never been able to get **full disk** encryption working on a bootable external drive.

---

### Post by sudodus on 2018-07-27
It is possble to get full disk encryption working on a bootable external drive.

One way is to unplug the internal drive and install Ubuntu (or like my demo: Lubuntu 18.04.1 LTS) according to this link:

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

after modification: Select 'Encrypt the new Lubuntu installation for security' (instead of the basic 'Erase disk and install Lubuntu').

See the attached screenshot.

This system was created (in UEFI mode) in a Toshiba laptop, and is portable enough to work well in an Intel NUC and other computers, that can boot in UEFI mode.

---

