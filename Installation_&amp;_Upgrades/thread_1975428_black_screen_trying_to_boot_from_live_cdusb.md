---
title: "black screen trying to boot from live cd/usb"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by famebu on 2012-05-07
Hello thank you for taking the time to help!

Whenever I try to boot Ubuntu or kubuntu 12.04 from live cd or usb I get stuck on a black screen with a hyphen blinking in the top left corner. I was able to get kubuntu 10.04 to boot from live cd but when I upgraded to 11.04 it would get stuck on the same black screen after reboot. I was thinking it may be because my graphics I have an hp pavilion p6774y which has built in gpu, but i have nvidia gtx 560ti also.  

Thank you for the help

---

### Post by 2F4U on 2012-05-07
Did you already try the solution outlined in this post?

[http://ubuntuforums.org/showthread.php?t=1975128](http://ubuntuforums.org/showthread.php?t=1975128)

---

### Post by famebu on 2012-05-08
2F4U thank you for the response!

I am new to doing all this but that says ATI, so will it work for nvidia or will i need to doing something else?

---

### Post by darkod on 2012-05-08
Try this first with nvidia:
Boot with the cd/usb but as soon as you see the first purple screen, hit Esc. That should bring up the older style main menu.

Hit F6 for advanced options, select nomodeset.

Then from the main menu select Try Ubuntu.

If that loads the desktop successfully, you can install but on first boot you will need to add that parameter manually so it can boot once and allow you to install the drivers.

To add the parameter, in the grub2 boot menu highlight the ubuntu entry and press 'e' for edit. That will show the boot lines. In the line starting with linux, go to the end and add nomodeset after the 'quiet splash'. Press Ctrl + X to boot. That should do it.

In most cases after installing the drivers the issue will go away.

---

### Post by famebu on 2012-05-08
> Try this first with nvidia:
Boot with the cd/usb but as soon as you see the first purple screen, hit Esc. That should bring up the older style main menu.

Hit F6 for advanced options, select nomodeset.

Then from the main menu select Try Ubuntu.

If that loads the desktop successfully, you can install but on first  boot you will need to add that parameter manually so it can boot once  and allow you to install the drivers.

To add the parameter, in the grub2 boot menu highlight the ubuntu entry  and press 'e' for edit. That will show the boot lines. In the line  starting with linux, go to the end and add nomodeset after the 'quiet  splash'. Press Ctrl + X to boot. That should do it.

In most cases after installing the drivers the issue will go away.

Fixed it completely boots with no problem.

Thank you for the help!

---

