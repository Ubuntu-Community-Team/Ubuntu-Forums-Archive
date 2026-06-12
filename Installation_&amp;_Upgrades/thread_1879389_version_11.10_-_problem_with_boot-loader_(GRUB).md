---
title: "version 11.10 - problem with boot-loader (GRUB)"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by bf1 on 2011-11-11
Hi!
I did download today version 11.10. from the offical server.After installaton on system with windows XP  this grub unable to load any system exept  ubuntu.  When I choose windows XP- it  make refresh and load ubuntu again. Please check it out and repair iso on your servers. 
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by drs305 on 2011-11-11
bf1,

Welcome to the Ubuntu Forums.

You may have installed Grub 2 to the Windows partition instead of the MBR. You can look at this site and see if the situation applies to you. It also details how to fix it:
[Boot Problems:Boot Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

If that does not fix it, please download and run the boot info script and post the contents of the RESULTS.txt it generates. It will show us what happened to your bootloader files.

Click on the "BIS" link in my signature line to go to the script's homepage.

---

### Post by Rubi1200 on 2011-11-11
+1 to the suggestions made by drs305!

Let's first see the boot info script before jumping to conclusions please.

---

### Post by bf1 on 2011-11-12
Thank you for answer, but:
1) I did go back from recovery image, so ubuntu is gone :) So, I am unable to provide any logs for now.
2)  I did the default installation, so in my opinioun ubuntu should prevent installing grub in windows sector by himself.
I have some research in the internet- the 11.10 version has many bugs, so I will wait for better version. I hope in the future  the  grub installation will be  more accurate  for default  installation process (mainly for newer users )
Thanks for understanding.
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by darkod on 2011-11-12
It is not a problem with ubuntu as much as with XP which is sensitive to other tools. If by default installation you let it resize the XP partition, that can create problems if chkdsk is not run BEFORE you install ubuntu. But the automatic process continues and this can happen.

It's better to run the live mode first, use Gparted to shrink your XP partition (if it's taking the whole HDD you have nowhere to install ubuntu). After all, it's your task to make unallocated space for it, the installer tries to help but issues can always happen.
After the XP partition has been resized, boot XP and do chkdsk, and again reboot XP few times.
Once it's happily working, you can do the ubuntu install into the unallocated space.

You can do the resize with any windows software you want also, but XP doesn't have a built-in tool for this.

---

