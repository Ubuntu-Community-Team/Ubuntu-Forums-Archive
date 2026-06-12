---
title: "Lenovo yoga 2 pro dual boot windows missing"
date: 2015-05-05
forum: Installation &amp; Upgrades
---

### Post by rspock on 2015-05-05
Hi there,



I tryed to dual boot my yoga 2 pro with windows 8.1 and ubuntu 14.04.



I did a couple of mistake: [****]("https://www.google.it/search?q=recognized&spell=1&sa=X&ei=kW5IVYnrKMjlUeX4gNAO&ved=0CBsQvwUoAA")

1)  I first installed ubuntu 32 bit so without efi support. All went fine  except that the windows partition was recognized but wasn't able to  boot.

2)After that I installed the 64bit  version but I suppouse I did some messy with the partition and now the  windows partition is not recognized at all.


I tryed to boot with boot repair disk and all the partition seems ok. This is my boot repair disk summary: [http://paste.ubuntu.com/10987173/](http://paste.ubuntu.com/10987173/)



P.S. I don't have the windows repair usb! :(

---

### Post by ubfan1 on 2015-05-05
Apparently, you changed EFI partitions, and the bootable sda2 one does not have the Windows bootloaders, which are still sitting in sda3.  Try just copying them over to the sda2 EFI (they are just files in directories).  See if the EFI menu (some function key at power-on to choose boot device/OS) runs Windows.  Then next time you are in Ubuntu, maybe run sudo update-grub if the Windows choice is not present.  Next boot, try selecting Windows from the grub menu, (and probably secure boot will need to be disabled for grub to boot Windows, even if Windows successfully boots from the EFI menu).

---

