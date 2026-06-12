---
title: "Install w/o GRUB"
date: 2018-09-27
forum: Installation &amp; Upgrades
---

### Post by uzaaft on 2018-09-27
Hello,
I am currently contemplating installing Ubuntu on my laptop. I've used Ubuntu before with ok results in achieving what I had in mind. My ideal situation would be to keep my system as is, with a windows boot menu and the choice to either boot in Ubuntu or Windows with Win being the preffered boot option, without GRUB. Is this possible, or do I have to install GRUB?

Thank you

---

### Post by oldfred on 2018-09-27
Grub2 is both a boot manager or menu and the boot loader.
You have to have grub to boot Ubuntu. There are some other boot loaders that can boot, but rarely used.

But if UEFI, you can just set Windows as first in boot order, and when you want Ubuntu use UEFI boot menu to choose Ubuntu.

Or with BIOS or UEFI, you can set Windows as default in grub menu and then only choose Ubuntu when you want Windows.

Do you have more than one drive? Most laptops only have one.
What brand/model system?

A few Windows users with BIOS use EasyBCD, but that is not required or recommended with UEFI.
And EasyBCD not really recommended with BIOS, as it uses the very old grub4dos to chain to another copy of grub. It then makes you install grub to a partition boot sector, which grub does not recommended as it is unreliable.

---

### Post by ubfan1 on 2018-09-27
Is Windows installed in UEFI mode? If so, grub installed in UEFI mode gets put into its own directory, /EFI/ubuntu, and does not interfere with Windows.  You can change the default bootloader order to put Windows first.  Adding Ubuntu to the Windows boot menu is possible, but a Windows site might be a better source for that information.  Or  use the EFI boot menu (some function key at power-up to allow choice of boot device/OS) to select Ubuntu instead of the default Windows.  
  It is possible to install (legacy) Ubuntu without grub, (with some trickery, like specifying a USB with an empty filesystem, and at the error dialog, select to proceed without a bootloader).  However, the last time I did this, I noticed a subtle error, on (kernel?) updates complaining about a missing libz library.  Now the library is not missing, it is just the last one in the library directory, so there is some problem, but not critical.  I'd suggest don't skip installing grub.

---

### Post by yancek on 2018-09-27
If you are using a newer windows with an EFI system, the suggestions above will do the job.  If you have an older Legacy/MBR install, you can boot Linux from windows with bcdedit but it is a rather convoluted process.  The two links below explain it in about as much detail as it is possible to give.  Much simpler to use Grub as the windows bootloader is designed specifically to boot windows and it gets cumbersome very quickly trying to boot anything else. 

[http://alien.slackbook.org/blog/adding-linux-to-the-windows7-boot-menu/](http://alien.slackbook.org/blog/adding-linux-to-the-windows7-boot-menu/)

[https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/)

---

