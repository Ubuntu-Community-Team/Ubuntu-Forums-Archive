---
title: "Win 7, Ubuntu 2 drives"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by brhokla on 2009-12-02
Quick Question. I have windows 7 64bit on a new machine, HP laptop. I have made my Ubunut 9.10 disk and would like to install it. I have a laptop with a internal 320gb 7200rpm drive and I also have a WD External HD hooked up through a usb port. Can I install Ubuntu to the external drive and partition only it leaving all my computers C drive for Windows 7 and half of the 320 external for backup and for Ubuntu? Will I get an option to install to the second drive or will the install go directly to my C: or drive 1? I also wonder what this will do when booting up when the external drive is not connected? Am I better off to partition about 40 GB's of the C drive where Windows 7 is installed?  Please advise as I'm a Ubuntu Rookie...

Thanks for any help.

---

### Post by darkod on 2009-12-02
You do have the option to install on the external hdd. The choice is yours.

You just have to pay attention and check that grub2 (the ubuntu bootloader) will be also installed on the external drive. Then in your computer BIOS you set 1st boot device USB HDD, 2nd boot device internal HDD.

When the usb hdd is plugged in, the computer will boot grub2 which will give you option to boot ubuntu or win7. If the usb hdd is not plugged in, the computer boots from the internal hdd which has only your win7 bootloader and win7.

---

