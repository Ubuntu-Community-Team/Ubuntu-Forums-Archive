---
title: "best parameters for Ubuntu 13.10 installation alongside win7"
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by ANKIT_RAJ on 2013-10-21
I have a system with win7 on C (225 GB), then two more drives (110 GB each with FAT32) and then an ext 4 type partition 21GB (which had Ubuntu 11.10 which is not booting since a month) and 4 GB swap area. I wanna install Ubuntu 13.10. But, specifically what parameters to choose in the Partition menu. I want to install 13.10 in the 21 GB space with earlier 11.10 on it. We have the following options when double clicking this partition [types       / , /boot, /home etc....] and different file systems. What specifically to choose for best performance.  Ofcourse I want my Win 7 intact.

---

### Post by fantab on 2013-10-21
When installing ubuntu and after choosing 'something else' option, select the 21gb partition and use the following:
USE As= Ext4
Mountpoint=/
Check/select to format.
Thats it.
One more thing: Install Grub bootloader to the HDD on which you install Ubuntu. Later in the BIOS change the default boot device to the HDD with Ubuntu. This way you won't corrupt the Windows MBR, because by default Grub will be installed to the first HDD, on which you probably have Windows.

Gook luck...

---

### Post by ANKIT_RAJ on 2013-10-21
I had Ubuntu 11.10 installed with which GRUB was automatically installed. Will formatting this 21GB partition remove this earlier installed GRUB. If yes, how to install it again. This GRUB tool was very handy for dual booting options.

---

### Post by fantab on 2013-10-22
When you select to Format that will erase whatever there was earlier on that partition. Yes Grub WILL be installed automatically, be we can choose where to install it. The option will be at the bottom of the dialog after you select 'Something Else'.
Were you booting into windows with Grub until now?

---

### Post by ANKIT_RAJ on 2013-10-22
Yes, I was booting to Win7 and Ubuntu selectively using GRUB till now. Thanks for the help.

---

### Post by ANKIT_RAJ on 2013-10-22
Installed Ubuntu 13.10 successfully. Working fine...

---

