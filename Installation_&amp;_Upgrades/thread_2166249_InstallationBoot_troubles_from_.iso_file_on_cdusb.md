---
title: "Installation/Boot troubles from .iso file on cd/usb"
date: 2013-08-08
forum: Installation &amp; Upgrades
---

### Post by wingarcher on 2013-08-08
Hello,

I have downloaded two 12.x (current LTS version for ubuntu desktop) .iso files and used them two different ways- once on a usb, once burned (properly) to a CD.

Windows 7 (formerly, big blow up, currently has a generic install but without driver support I'm going no-where) Dell Inspiron N7010.  About 2.5 years old.

I can access f12 to get it to boot from either the cd or the usb.  I get the purple screen with a graphic and can hit any key to pop up the options/menus.  

After that, or ignoring the options menu and allowing it to continue on its own, it shows the ubuntu graphic with 5 white/red dots underneath.  These cycle several times and then it invariably hangs and goes no further.  I did use the "verify disk" option and it checked the CD and did not return an error.  I have tried the "try ubuntu without installing option" as well as the install option.  Nothing ever gets all the way through.  The .iso files were downloaded separately and at different computers so I don't believe they are the issue.

Would love to get this installed (i've used older versions of ubuntu on previous machines) but can't seem to get very far!

Thx for help/suggestions in advance.

N

---

### Post by SlugSlug on 2013-08-08
Using ctrl+alt and the F keys (cycle through them) might give you some more clues (or perhaps just hitting Esc).

If it was me I'd try the latest version of Ubuntu

---

### Post by oldfred on 2013-08-08
Often related to video issues. What video card/chip do you have?

 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
Editing the GRUB 2 Menu During Boot
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

---

