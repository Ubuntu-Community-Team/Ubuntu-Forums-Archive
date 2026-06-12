---
title: "Acer Aspire ES-13, Windows 8"
date: 2015-01-22
forum: Installation &amp; Upgrades
---

### Post by Scott_Allison on 2015-01-22
Hello this is my first time ever installing another operating system. 

currently using acer aspire ES-13 on Windows 8 I downloaded the software from the offical website, then downloaded their USB installer as my computer has no CD-ROM drive. 

Follow the instructions and use the 3rd option of installation for computers without a CD-ROM drive. 

During the extraction process the install fails and displays the following error message, [IMG]http://s7.postimg.org/keumbvz57/Ubuntu_Install_Fail.jpg[/IMG]

If you require the info from the log file let me know. 

Any help would be greatly appreciated :) 

Thanks 

Scott

---

### Post by oldfred on 2015-01-22
That looks like  a wubi install. What instructions are you following.
Wubi is not supported anymore.

       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

You want to use Windows partition tools to shrink the Windows NTFS partition and reboot immediately to let it run chkdsk and make repairs for its new size.
You must have  fast boot or the always on hibernation off, and usually better to have secure boot off.

      
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)


 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

Other perhaps similar models:

 Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
black list some drivers for shutdown issues - post #9 link to Mint
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

