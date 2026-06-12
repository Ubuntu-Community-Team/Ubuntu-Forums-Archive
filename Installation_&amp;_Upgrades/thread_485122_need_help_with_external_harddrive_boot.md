---
title: "need help with external harddrive boot"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by JReagan1990 on 2007-06-26
I have installed Ubuntu on an external hard drive, with vista installed on the main machine.   Vista will not boot unless I have the external hard drive plugged in via USB because of Grub.  I have easyBCD installed on the vista partition, but when I restart my computer, grub comes up first, and then once I clicked on Vista, the easyBCD loads up.  Is there any way I can boot into vista without having the external hard drive plugged in?

---

### Post by confused57 on 2007-06-26
> **JReagan1990 said:**
> I have installed Ubuntu on an external hard drive, with vista installed on the main machine.   Vista will not boot unless I have the external hard drive plugged in via USB because of Grub.  I have easyBCD installed on the vista partition, but when I restart my computer, grub comes up first, and then once I clicked on Vista, the easyBCD loads up.  Is there any way I can boot into vista without having the external hard drive plugged in?
If you have a Vista install DVD, you can use it to restore your internal hard drive's mbr:
[http://www.windowsvista.windowsreinstall.com/vistaultimate/repairstartup/part1.htm](http://www.windowsvista.windowsreinstall.com/vistaultimate/repairstartup/part1.htm)

If you don't have an install DVD, you could use the MbrFix.exe:
[http://ubuntuforums.org/showpost.php?p=2802713&postcount=8](http://ubuntuforums.org/showpost.php?p=2802713&postcount=8)
[http://ubuntuforums.org/showpost.php?p=2809942&postcount=22](http://ubuntuforums.org/showpost.php?p=2809942&postcount=22)
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

I gave you these 3 links, so you might get a better understanding of MbrFix.exe.

---

