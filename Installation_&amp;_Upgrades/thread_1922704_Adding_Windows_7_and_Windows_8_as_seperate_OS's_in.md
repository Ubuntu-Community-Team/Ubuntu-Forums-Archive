---
title: "Adding Windows 7 and Windows 8 as seperate OS's in GRUB"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by Kiyamudeen on 2012-02-09
My laptop came with Windows 7 pre-installed, and later on I installed Windows 8 DP on it. Finally, I installed Ubuntu 11.10. 
 My problem is, GRUB gives me the option of booting into 'Windows 7', which actually loads up Windows 8 DP, and I have to load up Windows 7 from it's dual-boot selection.. Then my PC restarts, GRUB loads, and when I choose Windows 7 once more, I am eventually booted into Windows 7. What I want to do, is to show Windows 8 and Windows 7 as _two different OS selections_ in GRUB. Is this possible? I'm new to Ubuntu and am really needing help on this topic since it's being a time-waster for me... I've tried "update-grub" in the Terminal, but it still gives the same thing.. Help please?

---

### Post by Mark Phelps on 2012-02-09
The Win8 boot selection screen looks different from Win7 because it is an entirely NEW boot loader.  Linux stuff that used to work with Win7 does not work with Win8.

You can TRY to fix that by using the option in Win8 to select Win7 as the default OS.  What that actually does is switch you back to using the previous Win7 boot loader.

However, I don't think you can do what you want because GRUB will only point to a partition, and Win8 reused the Win7 partition to add its boot loader stuff.

Also, the Win8 Consumer Preview (MS's NEW term for BETA) is coming out on the 29th.  So, I would leave it alone for now and consider removing Win8 DP and replacing it with Win8 CP.  That is likely to have even MORE changes to the boot loader.

---

### Post by Kiyamudeen on 2012-02-09
I suppose I better wait, then. Besides, I have no idea of how to change the default OS.. I checked through the Control Panel, but no help... :( Anyway, there's no way of me removing Win8 DP, is there? MS told it's uninstallable, and I'm pretty sure it's not possible to 'remove' an OS... Formatting would ruin my files, wouldn't they? :|

---

### Post by mebomechanicno1 on 2012-02-09
> **Kiyamudeen said:**
> I suppose I better wait, then. Besides, I have no idea of how to change the default OS.. I checked through the Control Panel, but no help... :( Anyway, there's no way of me removing Win8 DP, is there? MS told it's uninstallable, and I'm pretty sure it's not possible to 'remove' an OS... Formatting would ruin my files, wouldn't they? :|
 
Unfortunately, "No" and "Yes", and even if you do manage a "quick fix" there is no guarantee GRUB will not continue to point to the partition where WIN 8 used to be. You may have no option but to salvage what you can then format and re-install, unless somebody out there knows better?

---

### Post by oldfred on 2012-02-09
As long as you are booting with BIOS/MBR, I bet Windows 8 works similar to Vista/7. It combines all boots into one partition that is the boot partition or active partition. You may be able to move boot flag and run repairs if both installs are in primary paritions.

To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by Kiyamudeen on 2012-02-11
Thanks for the replies, guys, but I managed to uninstall Windows 8 DP today... Thanks for your support, anyway.. ;)

---

