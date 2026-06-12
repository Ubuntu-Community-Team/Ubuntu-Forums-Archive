---
title: "Boot-repair didn't allow me to boot to ubuntu 14.10"
date: 2015-01-03
forum: Installation &amp; Upgrades
---

### Post by alex308 on 2015-01-03
Hi all. Very new to ubuntu, and would appreciate your help. I successfully created a partition and installed ubuntu on a cheap Acer laptop ([Acer-Aspire-ES1-512-C88M-15-6-Inch-]("http://www.amazon.com/Acer-Aspire-ES1-512-C88M-15-6-Inch-Diamond/dp/B00MNOPS1W/ref=sr_1_12?s=pc&ie=UTF8&qid=1417775709&sr=1-12")) running Windows 8.1 It wouldn't allow me to boot to ubuntu, so I used the USB to run the boot-repair's recommended repairs. Still nothing. I followed the suggestion directly following the repair, and tried to the Windows command prompt with boot manager, but was still unsuccessful. I changed the boot order in BIOS to move the HD ahead of Windows boot, but there's nothing there relating to ubuntu.

The generated report: paste.ubuntu.com/9664370

Thanks in advance for your help. I turned off secure boot at the advice of the boot-repair tool.

---

### Post by oldfred on 2015-01-03
Clicky link
[http://paste.ubuntu.com/9664370/](http://paste.ubuntu.com/9664370/)

What model Acer?

Did you try the suggestion of adding Ubuntu to Window's BCD with bcdedit?

       Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

      How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)

Do not reinstall Ubuntu without using Something Else. And make a full backup of Windows before doing anything else. More details in link in my signature.

Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)
Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)
Herman's 2014_02_09 - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop
[http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html](http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html)

---

### Post by alex308 on 2015-01-04
Thanks for the links. I will give some of them a go and report back.

The final link seemed to be the most relevant to my problem, so I went into UEFI and enabled shim, grub, and ubuntu, but the computer still boots directly to Windows. Working on some of the other ideas now.

---

### Post by alex308 on 2015-01-04
So after this I was able to change the boot order, and now have the option to choose Ubuntu. However, when I do a get a purple screen that doesn't end. I restarted and picked a different version of the installation, got a couple error messages, but the different version seemed to start fine, but when I shut down I got an ubuntu screen that loaded forever until I manually shut it down. Any suggestions? Thanks for that final link in particular - I definitely never would have figured it out without that!

---

### Post by oldfred on 2015-01-04
What video chip does your Acer have?

If Intel, nomodeset does not usually work, but one of the options in post by ubfan1 may.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

