---
title: "Boots straight to Windows"
date: 2017-03-24
forum: Installation &amp; Upgrades
---

### Post by carpenter.katie.e on 2017-03-24
Sorry if this is a redundant question, but I'm not sure exactly how to search the forums for my problem. I just did a fresh dual-boot install of Ubuntu 16.04 from a live USB on my new Acer laptop running Windows 10. When I start up the computer without the USB in (in fact, even when it is in--I have to go into the F12 menu, as no changing of the boot order makes the USB work first), Windows boots up right away. I ran boot-repair, which suggested I disable Secure Boot. I did that, ran it again, and got this code: [http://paste2.org/eCIa7tb8](http://paste2.org/eCIa7tb8) 

Can anyone help me interpret?? Thanks so much in advance.

---

### Post by ubfan1 on 2017-03-24
Acer wants you to set a supervisor password in the UEFI Settings/BIOS, then additional options are available, and things like resetting boot order may work better too.  You can also try the EFI boot menu, some function key at power on to select the boot device/OS.  Choose Ubuntu, or maybe hdd, then another set of choices with ubuntu.  Looks like after running boot-repair, you do have ubuntu as the first item in the bootorder, with shim, so that should work with or without secure boot.

---

### Post by RobGoss on 2017-03-24
Hello and welcome, Please see this post by OldFred he has some good information on Dual booting with Acer, check post **#2 **[https://ubuntuforums.org/showthread.php?t=2292563](https://ubuntuforums.org/showthread.php?t=2292563)

As **Ubfran **pointed out setting a supervisor password should do the trick the manufacturers made it a bit harder to install Linux on those machine

---

### Post by carpenter.katie.e on 2017-03-25
It's working! Thank you both!!

What I had already done was set a supervisor password and then disabled Secure Boot, but what I wouldn't have thought to do was ENABLE Secure Boot and add all the Ubuntu efi's as "trusted for executing" (that option is grayed-out when Secure Boot is disabled), THEN disable Secure Boot. Now those 3 or 4 ubuntu efi's show up in the boot menu list. I've moved them to the top, and the computer boots straight to the Ubuntu grub menu.
Very helpful forum link, RobGoss.

---

### Post by RobGoss on 2017-03-25
> **carpenter.katie.e said:**
> It's working! Thank you both!!

What I had already done was set a supervisor password and then disabled Secure Boot, but what I wouldn't have thought to do was ENABLE Secure Boot and add all the Ubuntu efi's as "trusted for executing" (that option is grayed-out when Secure Boot is disabled), THEN disable Secure Boot. Now those 3 or 4 ubuntu efi's show up in the boot menu list. I've moved them to the top, and the computer boots straight to the Ubuntu grub menu.
Very helpful forum link, RobGoss.

That's great, yes Acer is a bit harder to install Ubuntu or other distributions after making those changes it seems to work as intended 

Thank you for letting us know you were successful with your installation

If you solved your issue you may mark this thread as solved, you can do this by using the **Thread tool** tab at the top of this page, and again welcome to the Ubuntu forum

---

