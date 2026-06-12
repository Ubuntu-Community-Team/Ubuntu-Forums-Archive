---
title: "Vista disapeared from the operating system list on my PC when I upgraded Ubuntu"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by eessay on 2009-12-28
Hi There

Please help! How can I gain access to Windows Vista which is installed on my Sony Vaio desktop. I upgraded my Ubuntu to 9.04 which is also installed on the same PC. I have Vista and Ubuntu on the same machine. Ever since I upgraded to 9.04 Vista disappeared from the booting list. How can I get Vista back on the list of operating systems on my PC?  

Thanks in advance!

Regards
Eessay

---

### Post by sliketymo on 2009-12-28
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by TrevT93 on 2009-12-28
So you're saying that Vista and Ubuntu were both installed and you were booting off the GRUB boot menu, and when you updated to 9.04 Vista disappeared off the menu?

You should be able to get it back by booting into Ubuntu and running "sudo update-grub" in a terminal (without the quotes).  After doing so reboot your computer to see if the menu's changed.

If this doesn't work, we can do it manually.

---

### Post by presence1960 on 2009-12-28
> **eessay said:**
> Hi There

Please help! How can I gain access to Windows Vista which is installed on my Sony Vaio desktop. I upgraded my Ubuntu to 9.04 which is also installed on the same PC. I have Vista and Ubuntu on the same machine. Ever since I upgraded to 9.04 Vista disappeared from the booting list. How can I get Vista back on the list of operating systems on my PC?  

Thanks in advance!

Regards
Eessay

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

