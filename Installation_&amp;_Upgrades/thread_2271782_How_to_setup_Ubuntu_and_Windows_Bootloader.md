---
title: "How to setup Ubuntu and Windows Bootloader"
date: 2015-04-01
forum: Installation &amp; Upgrades
---

### Post by BinaryJava on 2015-04-01
Hello there,

I was wondering about what is the best way to setup my bootloader. I want to use the windows 8.1 bootloader instead of GRUB since I will be prioritising windows. Currently my system loads up GRUB and gives me the option to boot straight into Ubuntu or windows boot manager. My windows boot manager does not detect my Linux OS so it just takes me longer to boot into windows.

Should I try to use the windows boot manager, or use GRUB and fix the windows boot manager thing?

How would I go about doing it?

-Binary

---

### Post by BinaryJava on 2015-04-01
What does your bootloader look like?

---

### Post by yancek on 2015-04-01
A windows bootloader will not detect a Linux system.  You can configure the windows boot files to boot Linux but it is considerably more complex than using Grub.  An option is to use third party software such as EasyBCD on windows to boot.  I don't know if it will work with EFI or if you are using EFI to boot.  In a standard system with Grub, you would simply set the windows boot entry to default in the /etc/default/grub file and run:  sudo update-grub.  If you are using EFI, I'm not really sure this would work so best wait for someone else if you are using EFI.

---

