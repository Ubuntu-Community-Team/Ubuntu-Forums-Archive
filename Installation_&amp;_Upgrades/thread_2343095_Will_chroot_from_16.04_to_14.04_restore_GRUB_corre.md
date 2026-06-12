---
title: "Will chroot from 16.04 to 14.04 restore GRUB correctly?"
date: 2016-11-13
forum: Installation &amp; Upgrades
---

### Post by Petr_Be on 2016-11-13
Hello everyone,

a friend of mine will be installing Win 7 on his computer, he needs it for some DJ software.

He already has Ubuntu 14.04 installed on that computer and he wants to keep it. He also has a free partition ready for Windows, so there is no need to repartition the drive.

I am aware that Windows will replace Grub with its own bootloader, which can only boot Windows. Therefore, I will boot Ubuntu 16.04 from a USB drive, chroot to the existing Ubuntu installation and reinstall Grub from there.

My question is: will there be any compatibility issues when the system installed on the computer is 14.04 while the USB drive has 16.04? Are the versions of kernel and Grub in 14.04 and 16.04 close enough for the chroot method not to break anything? Or is it safer to create a 14.04 USB drive for this purpose?

Thank you very much

Petr B&#345;e&#328;

---

### Post by ajgreeny on 2016-11-13
It will be much easier to use **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and someone will be able to give you advice on how to do what you want.

---

