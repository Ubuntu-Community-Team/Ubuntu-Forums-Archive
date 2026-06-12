---
title: "grub boot loader"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by james2b on 2008-10-02
Since I had seen some forums posts about the Ubuntu 8.04 install process that had cleared the partition table. So then is this grub related bug now fixed in the newest Ubuntu 8.04.1 version? Also during the install, is there any grub boot loader install options available such as where (MBR or other), and to not install grub?

---

### Post by Herman on 2008-10-03
I think you are probably referring to the bug that can be read about in the [Apple Users]("http://ubuntuforums.org/forumdisplay.php?f=328") section of the Ubuntu Web Forums, in the                                                                 [Apple Intel Users FAQ]("http://ubuntuforums.org/showthread.php?t=493393").
> [B][COLOR=DarkRed][SIZE=4]HARDY BUG:
[/SIZE][/COLOR][/B][COLOR=Black][SIZE=4][SIZE=2]If you have problems booting Ubuntu after installing Ubuntu 8.04, please see this link. There is a bug in the Ubuntu installer.
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)[/SIZE][/SIZE][/COLOR]Is that the one you are referring to? :D

If it is, then you have nothing to worry about unless you own a Apple computer.
That bug only applies to Apple Macs.

You can select a device to install GRUB to if you are using the Live 'Desktop' CD, by pressing the 'advanced' button in step 7 of 7.
You can select a device to install GRUB to, or select to use LiLo instead, or even continue with the installation without any boot loader at all, with the 'Alternate' CD, by choosing 'No' when asked if you want to install the GRUB boot loader to the Master Boot Record.
Here's a link about that, [Installing a Boot Loader for Ubuntu]("http://users.bigpond.net.au/hermanzone/p6.htm#Installing_a_Boot_Loader_for_Ubuntu").

I think GRUB is by far the best boot loader for most people.

Regards, Herman :D

---

### Post by james2b on 2008-10-03
Yes that is the install bug, only for Apple users then, thanks. And I did just finish the Ubuntu 8.04.1 install process last night, and I did click that advanced button on step 7, but just to look, as the options looked fine. But 1 question now is how do I get the Grub graphical screen, as now it is only plain text type? So is there a boot loader grub splash image file some where that I can just add into a folder, and then edit the menu.lst boot file? A separate issue is my Dell LCD monitor is not correctly detected and configured, since the screen Power Manager, and Screen Saver do not fully function correctly. It is a Dell 1704FPT and connected DVI digital, not analog VGA. Thanks, Jim

---

### Post by Herman on 2008-10-03
> Yes that is the install bug, only for Apple users then, thanks. And I did just finish the Ubuntu 8.04.1 install process last night, and I did click that advanced button on step 7, but just to look, as the options looked fine.:D Cool!
> But 1 question now is how do I get the Grub graphical screen, as now it is only plain text type? So is there a boot loader grub splash image file some where that I can just add into a folder, and then edit the menu.lst boot file?Yes, that's basically right. You can download one from somewhere on the internet, or make your very own unique personal splashimage.
You just need to add a line to your /boot/grub/menu.lst file to get it to show up.
Here's a link to my collection of information about GRUB and splashimages,  [splashimage]("http://users.bigpond.net.au/hermanzone/p15.htm#splash").  - make your GRUB menu beautiful! Full instructions!
> A separate issue is my Dell LCD monitor is not correctly detected and configured, since the screen Power Manager, and Screen Saver do not fully function correctly.
:-k Hmmm, I'm no expert on Xserver issues, but I'll see if I can find any information that might be helpful about that for you and post back here with it later.

EDIT: Mmmm, very nice! [Dell 1704FPT Documentation]("http://support.dell.com/support/edocs/monitors/1704fpt/EN/about.htm").

EDIT 2: How about this, [[SOLVED] DEll 1704FPT monitor  resolution issues]("http://ubuntuforums.org/showthread.php?t=661270&highlight=Dell+1704FPT") ?

---

