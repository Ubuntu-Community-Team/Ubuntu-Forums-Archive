---
title: "Windows 7 on Grub boot loader"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by jkapera1988 on 2010-04-04
On my computer I had Windows 7 on one partition and XP on another. I got rid of the XP partition and replaced it with Ubuntu. But now when I boot up my computer the Grub boot loader only detects Ubuntu and not Windows 7. What do I do to fix it?

---

### Post by byStanderone on 2010-04-04
...try on an ubuntu terminal sudo update-grub

---

### Post by jkapera1988 on 2010-04-04
I tried that. It said it updated the menu list but it didn't. I tried creating another user account with admin rights but still no go. At startup I have to press esc to get into the grub menu. If i don't it boots straight to ubuntu.

---

### Post by oldfred on 2010-04-04
Windows only knows how to boot from one primary partition. It combines its boot to that partition.

[http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products](http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products)
louieb's suggestion:
Just a note about dual booting 2 MS products. When you install the 2nd one - the installer will put its boot loader in the partition with the boot flag on (usually the partition holding the 1st MS product). And the 2nd product can only be booted thru the boot loader in the 1st product.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

You may have to run repairs on your win7 install if it is in a primary partition. Then after windows works reinstall grub and sudo update-grub will find it.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

