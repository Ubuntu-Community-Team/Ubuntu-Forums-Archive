---
title: "Installing Ubuntu to a portable Hardrive question."
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by Gene393 on 2011-08-09
Hello, Im just wondering if there is anyway to install Ubntu, preferably 11.04, to an external hard rive in such a way as grub does not look for it on startup, and instead make it bootable?

---

### Post by Nearl-86 on 2011-08-10
I should have asked this question before I tried this now I cant even boot up without having the external attached to my computer. If you like, if or when I find a fix I will post it here for you.

---

### Post by Hakunka-Matata on 2011-08-10
@Nearl-86:  What is the OS on your main computer?  Windows?  

[LIST]
[*]The MBR - boot sector of the operating system on your internal hard drive has been overwritten by Ubuntu's Grub bootloader likely.  If that's the case, it's a simple matter to restore/repair the boot sector and then you will be able to boot to one or the other by changing your BIOS settings "First Boot Drive".
[*]If your other OS is Windows7, see bottom link in my signature,
[*]if it's WindowsXP, search the forums for "fixmbr"
[/LIST]

---

### Post by YesWeCan on 2011-08-10
[http://ubuntuforums.org/showthread.php?p=11137022#post11137022](http://ubuntuforums.org/showthread.php?p=11137022#post11137022)

---

