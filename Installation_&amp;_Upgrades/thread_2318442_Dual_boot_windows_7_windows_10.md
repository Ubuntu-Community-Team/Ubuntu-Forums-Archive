---
title: "Dual boot windows 7 windows 10"
date: 2016-03-26
forum: Installation &amp; Upgrades
---

### Post by Brian_G_M on 2016-03-26
Hi,
I want to install Ubuntu on a laptop to dual boot with windows. 
The laptop is running windows 7. But I recently upgraded to windows 10, had problems with that and reverted to windows 7.
Now ubuntu thinks I am running windows 10. It offers to install ubuntu inside windows 10. Can I just go ahead with that, will it work with windows 7?
If not, what do I do?
Thanks for your help,
Brian

---

### Post by RobGoss on 2016-03-26
Hello and welcome, If you want to install Ubuntu as a dual boot and choose Alongside of Windows Ubuntu live CD will help configure these options for you.

I recommend reading this before you attempt to dual boot it has a lot of good information.. [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Brian_G_M on 2016-03-26
OK, thanks, but is it an issue that I am running windows 7 but ubuntu thinks I am running windows 10?

---

### Post by RobGoss on 2016-03-26
It should not be a problem as far as I can tell.

---

### Post by Bucky Ball on 2016-03-26
Probably not. 

[QUOTE=Brian_G_M ] It offers to install ubuntu inside windows 10.[/QUOTE]

Do not go for that. It is a Wubi install. That is Ubuntu inside Windows, no longer supported, not a dual-boot, avoid.

---

### Post by oldfred on 2016-03-26
Not sure how grub scans NTFS to know version.
It was that grub was not updated to find Windows 10, and it would parse thru versions and if no match it was a recovery partition.

When I had XP I had used a Windows 7 repair flash drive to run chkdsk. And that left Windows 7 as various bits of info.

If your Windows boots ok, then not an issue.

If you really want correct description, you can copy Windows boot stanza to 40_custom, edit description to what you want and turn off os-prober so it does not find anything.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

