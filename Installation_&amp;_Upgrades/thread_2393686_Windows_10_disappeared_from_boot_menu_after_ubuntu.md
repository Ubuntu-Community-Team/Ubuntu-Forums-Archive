---
title: "Windows 10 disappeared from boot menu after ubuntu 18.04 install"
date: 2018-06-06
forum: Installation &amp; Upgrades
---

### Post by nocom2 on 2018-06-06
I had a dual setup in which first Windows 10 was installed and after that Linux Mint 18.3. Because Mint started to behave erratically when I inserted a new Nvidia graphics card I decided to give Ubuntu 18.04 a try. Created some space on the disk, booted from USB and installed. After reboot I noticed that the Windows 10 option had disappeared from the boot menu. Linux Mint still existed. When I look with Gparted I see that the Windows partition still exists. I can access the Windows and Mint partitions. Fdisk -l gives the following results:

```
Device             Start       End   Sectors   Size Type
/dev/nvme0n1p1      2048    923647    921600   450M Windows recovery environment
/dev/nvme0n1p2    923648   1126399    202752    99M EFI System
/dev/nvme0n1p3   1126400   1159167     32768    16M Microsoft reserved
/dev/nvme0n1p4   1159168 484268031 483108864 230,4G Microsoft basic data
/dev/nvme0n1p5 573440000 933367807 359927808 171,6G Linux filesystem
/dev/nvme0n1p6 484268032 484270079      2048     1M BIOS boot
/dev/nvme0n1p7 484270080 573439999  89169920  42,5G Linux filesystem
```

/dev/nvme0n1p4 is the Windows partition. I tried this:

 
 
```
sudo update-grub
sudo grub-install /dev/nvme0n1p4
```

That didn’t help. I tried to run os-prober, but that saw only the Mint partition. 
I saw a lot of advice but they differed greatly in content and quality. If somebody could point me to 
some reliable answer I would greatly appreciate that.

Thanks for your time.

---

### Post by oldfred on 2018-06-06
It looks like you have a bios_grub partition.
The installer only creates that for BIOS boot on gpt partitioned drives.
But you also have an ESP - efi system partition for UEFI boot.

UEFI & BIOS are not compatible. They write hardware info differently onto drive for operating system. Or you can only boot from UEFI boot menu. Or grub only can boot other installs in same boot mode.

You can easily convert your install to UEFI boot by uninstalling the BIOS grub version and installing the UEFI grub version. Boot Ubuntu install in UEFI mode, add Boot-Repair and in advanced options run the full uninstall/reinstall of grub.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by nocom2 on 2018-06-11
Thank you oldfred, that helped. First time I did the default repair, that refused at the last step. Later on I did as you advised (using  the advanced option) and that worked. Great tool, great tip. Thanks!

---

