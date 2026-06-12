---
title: "Error 18 fixmbr"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by lamdis on 2010-01-21
Installed windows xp on new ata Hdd and added ubunto next; got error 18 ; used the Fixmbr at the win console for repair; able now to access my windows but not the Ubunto; I guess Grub removed on repair. Would like to bring ubunto back.
Any advice greatly appreciated
Many thanks

---

### Post by presence1960 on 2010-01-21
I need two things: make & model of your machine & the manufacture date if known. Then I need more info about your setup & boot process. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Error 18 is usually a result of an older BIOS not being able to read past a certain point on the hard disk. If files needed to boot are beyond that boundary you will get Error 18. There are two ways to fix this. Either update your BIOS if an update which can fix that limitation is available or when you install Ubuntu make a 100-200 MB /boot partition at the beginning of the disk.

---

