---
title: "Overwriting Win8"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by canadianwriterman on 2013-05-09
I've been reading the posts and help guides on installing on a UEFI machine, but they seem to all talk about installing **alongside** Windows. I have a brand-new Toshiba Satellite 850 laptop with Win8 pre-installed. It boots very fast, so I assume it has UEFI and the other boot aides. I want to install Xubuntu 13.04 to **erase Win8** so that Xubuntu is the only OS. Do I have to disable anything on the machine? Thanks for your help.

---

### Post by ajgreeny on 2013-05-09
You probably need to make sure that Win8 is fully shutdown, not just in its default hybrid/hibernation, or whatever it's called.  I have no idea how you manage that as I have not used, nor even seen Win8 other than in the shops.

---

### Post by oldfred on 2013-05-09
One or two users have done it. But I do not recommend it unless you are sure your system does not have settings that prevent Linux from installing correctly and working. Best to start with dual boot.

A few systems just will not install Ubuntu. Many only install with secure boot on. If you do not need secure boot( I do not think you do) you should be able to boot and use just Ubuntu. Some with UEFI only boot Windows or the Windows efi file. So then Ubuntu has to rename the Windows efi file to really be grub's efi file.

You should also be able to totally turn UEFI off and boot in CSM (BIOS) mode. Ubuntu will boot from a gpt partitioned drive in BIOS mode if you add a tiny 1MB unformatted partition with the bios_grub flag.
       Compatibility Support Module (CSM), which emulates a BIOS mode

You do have to make sure UEFI has fast boot off, as a few system can only get into UEFI from Windows with UEFI fast boot on. If Windows does not boot then you have a brick and with Windows not always working on its own that does not seem like a good UEFI design anyway. You may need to get into UEFI to boot a Windows repair drive.

      
 Toshiba laptop C850 Windows 7 with upgrade to 8 version -  sudodus
[http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025](http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025)

I would at the very least backup Windows 8 and the efi partition before installing.
      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

How you boot Ubuntu flash drive installer is how it installs, either UEFI or BIOS.

---

### Post by canadianwriterman on 2013-05-09
Thank you all, for your responses. It sounds complex and risky. I'd hate to end up with an upbootable system Damn MS anyway!

---

### Post by arpanaut on 2013-05-09
>  Damn MS anyway!                         

Not necessarily MS fault, each hardware distributor has it's own implementation of uefi and may not have any concern about their hardware being able to boot anything other than what they ship/ how they ship it.

It's a very new technology and there is not any standard implementation established.
I  jut installed 13.04 on a Lenovo tower, and had very few problems getting it to dual boot, except grub did not write the windows boot entry correctly, boot-repair did it's magic and off I went.

It is a bit of a crap shoot as to what hardware is going to work correctly, but it is not necessarily a matter of it being the fault of MS.
It is a good technology, it is just going to take the manufacturers time to catch up. Complain to your equipment&#8217;s manufacturer.

---

### Post by MartyBuntu on 2013-05-09
Just do a drive image before you proceed. That way you can revert back to Windows 8 for re-sell or troubleshooting.

Once you have your full backup, disable UEFI in the BIOS. Your Ubuntu installation should go smoothly.

---

### Post by oldfred on 2013-05-10
+1 on MartyBuntu's suggestion.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)



UltraBook with SSD, and erased Windows and installed Ubuntu to SSD.
 Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

---

