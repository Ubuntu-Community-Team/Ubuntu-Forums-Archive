---
title: "How can I boots straight to windows?"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by JackTar1000 on 2008-02-17
Can someone please help me before my wife torches the computer? I have installed Ubuntu 7.10 on a USB Hard drive and I wanted it to only come up when I booted to that hard drive however it straight away comes up with the menu which allows you to go to Ubuntu or windows which drives my wife crazy because she likes to turn the computer on then do something else while it starts. If I just turn the USB HDD off I get grub error messages and the system won't boot at all. Is there a way I can make it go to Ubuntu only if I have the USB HDD on or at least move windows vista to the top of the boot menu so that it does not go straight into Ubuntu if left alon?

---

### Post by QwUo173Hy on 2008-02-17
You can easily make Windows the default instead of ubuntu by editing /boot/grub/menu.lst

The line you need to change is:
> default         0
Here, 0 means the first entry. So if Windows is 2nd on  your list change it to a 1 and if it's 3rd on the list, change it to 2 and so on.

---

### Post by overdrank on 2008-02-17
> **JackTar1000 said:**
> Can someone please help me before my wife torches the computer? I have installed Ubuntu 7.10 on a USB Hard drive and I wanted it to only come up when I booted to that hard drive however it straight away comes up with the menu which allows you to go to Ubuntu or windows which drives my wife crazy because she likes to turn the computer on then do something else while it starts. If I just turn the USB HDD off I get grub error messages and the system won't boot at all. Is there a way I can make it go to Ubuntu only if I have the USB HDD on or at least move windows vista to the top of the boot menu so that it does not go straight into Ubuntu if left alon?

HI and you can edit your grub menu list to set windows as default or you can reinstall the grub to the main drive and here is a good link
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Edit to slow :)

---

### Post by scottbporter on 2008-02-17
It's a matter of editing your menu.lst file. You have to open it as root. It is located in "root"/boot/grub directory. You can go to the terminal window and do sudo gedit menu.lst (making sure to first manually change to the /boot/grub directory. if you cannot do this, got to AUTOMATIX home page, download it and let it install the scripts, one of which allows you to right click on file and run gedit as root. 

Once the file is open for editing, count down to the number where windows is (starting with 0 first), then go back to section at top of file that I believe says default= and replace probably 0 with that number.

---

### Post by QwUo173Hy on 2008-02-17
Yes, I forgot to mention that you need to be root.

Type

> sudo gedit /boot/grub/menu.lst

to easily edit the file.. Be VERY careful with this file. Just edit what you need, save and exit.

---

### Post by confused57 on 2008-02-17
> **JackTar1000 said:**
> Can someone please help me before my wife torches the computer? I have installed Ubuntu 7.10 on a USB Hard drive and I wanted it to only come up when I booted to that hard drive however it straight away comes up with the menu which allows you to go to Ubuntu or windows which drives my wife crazy because she likes to turn the computer on then do something else while it starts. If I just turn the USB HDD off I get grub error messages and the system won't boot at all. Is there a way I can make it go to Ubuntu only if I have the USB HDD on or at least move windows vista to the top of the boot menu so that it does not go straight into Ubuntu if left alon?
What's happened is that you installed grub's IPL(Initial Program Loader)  to the mbr of the internal hard drive, which is why you're not able to boot Vista with the external drive disconnected.  If you have a Vista install DVD(not a recovery cd), you can reinstall Vista's IPL to the internal hard:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If you don't have a Vista install DVD, you can use Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Then you can set Vista up to boot Ubuntu on your external drive, using EasyBCD:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

In order to boot Ubuntu from Vista, grub needs to be installed to the root partition on the external drive, which is easy to do with the Ubuntu live cd:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

