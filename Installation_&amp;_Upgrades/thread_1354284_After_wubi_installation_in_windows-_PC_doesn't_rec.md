---
title: "After wubi installation in windows- PC doesn't recognise it upon reboot"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by chumchum on 2009-12-13
Hi
I've installed the latest version of wubi on my external hard disk, after the installation I was prompted to restart the PC, did so but nothing changed, it just boots immediately into windows as though wubi were never installed. Ubuntu does however appear in Windows list of installed programs.

Any help?

thanks

---

### Post by garvinrick4 on 2009-12-13
Is it on the same partition where a Windows OS resides. It has to attach itself to
windows Dos4Grub so it has a boot option. It resides as a folder inside of Windows right
next to Users in C: Drive.

If it is what version of Windows.  Vista or 7 you can use this code in command line and you
have to right click and select administrator.
CODE:
"bcdedit"     without quotes.

That will show you your windows Grub and the last one should be a short one with WUBI in it. It will say so.

Post if problem.

---

### Post by chumchum on 2009-12-15
The windows version is XP
I've installed it on the J Hard disk and Windows is installed on C.

---

### Post by presence1960 on 2009-12-15
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with your external HD plugged in. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

P.S. is chumchum from Fanboy & ChumChum?

---

