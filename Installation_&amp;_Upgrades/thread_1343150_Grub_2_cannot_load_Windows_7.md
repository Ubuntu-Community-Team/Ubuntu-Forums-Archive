---
title: "Grub 2 cannot load Windows 7"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by chupi on 2009-12-01
Hello,

I recently set-up Windows 7 Enterprise N edition on my Dell Latitude 630 laptop on a 160GB NTFS parition. After loading Windows and all applications, I installed Ubuntu and created an additional 120GB partition for Ubuntu. The install went smooth and everything worked until....
After editing the: /etc/default/grub
GRUB_DEFAULT=0 (Ubuntu) and changed this value to 6 (Windows 7)so Grub default to Windows 7 instead of Ubuntu which worked. The problem was when I edited the timeout during the Grub OS splashscreen to:
GRUB_TIMEOUT="0"
I could not access my Ubuntu install by pressing shift or escape key sequences as explained in Grub 2 documentation.
I was able to use the Grub Live CD to change the Timeout value.
But now I cannot access my Windows 7 Partition from the OS menu. 
I've tried re-installing Ubuntu by overwritting the existing Ubuntu partition and importing all files. Now when I try to access Windows 7. The screen will hang and only allow me in Ubuntu. All Windows Folder/Files are there but Grub cannot access the OS. How can I relink Grub 2 to my Windows 7 install?

---

### Post by darkod on 2009-12-01
I didn't understand what you actually did with reinstalling ubuntu, and there was no need for it since ubuntu itself is fine, you played with the grub2 config a bit.
But in order grub2 to scan for other OS on the drive in terminal do:
sudo update-grub

---

