---
title: "Help! USB recovery"
date: 2012-08-09
forum: Installation &amp; Upgrades
---

### Post by Gootch on 2012-08-09
Hey guys.


I need to fix my PC because I wiped the Ubuntu partition and now I get the Error partition not found grub rescue. I need to instal Boot Repair on a USB.


How should I do this so I can get windows 7 running again


1 member has helped me on my previous thread and he said this is what I should do.

---

### Post by drmrgd on 2012-08-09
Just to clarify, are you intending on completely removing Ubuntu and only running Windows 7, or do you intend to re-install Ubuntu?  If you want to completely remove Ubuntu, then running Boot Repair is not going to help; using the Windows Boot manager would be better in this case.  If you deleted the Ubuntu partition but still want Ubuntu on your system, you'll need to reinstall Ubuntu of course, and then depending on the way your system is set up, Grub may be automatically fixed upon reinstallation.

At any rate, in answer to your question about making a bootable Boot Repair USB, grab the .iso file from this location:

[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

Then use the .iso to create a bootable USB using software such as UNetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

That would create a Boot Repair USB drive that you can boot to.

---

### Post by Gootch on 2012-08-09
> **drmrgd said:**
> Just to clarify, are you intending on completely removing Ubuntu and only running Windows 7, or do you intend to re-install Ubuntu?  If you want to completely remove Ubuntu, then running Boot Repair is not going to help; using the Windows Boot manager would be better in this case.  If you deleted the Ubuntu partition but still want Ubuntu on your system, you'll need to reinstall Ubuntu of course, and then depending on the way your system is set up, Grub may be automatically fixed upon reinstallation.

At any rate, in answer to your question about making a bootable Boot Repair USB, grab the .iso file from this location:

[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

Then use the .iso to create a bootable USB using software such as UNetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

That would create a Boot Repair USB drive that you can boot to.

What I want to do is repair my boot so I can run windows. I don't want ubuntu.

---

### Post by lkraemer on 2012-08-09
If I were in your situation, I would use SuperGrub:
[http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)
[http://www.supergrubdisk.org/2011/05/02/tutorial-fixing-the-boot-loader-with-rescatux/](http://www.supergrubdisk.org/2011/05/02/tutorial-fixing-the-boot-loader-with-rescatux/)

It should do exactly what you need.

Larry

---

### Post by Gootch on 2012-08-09
> **lkraemer said:**
> If I were in your situation, I would use SuperGrub:
[http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)
[http://www.supergrubdisk.org/2011/05/02/tutorial-fixing-the-boot-loader-with-rescatux/](http://www.supergrubdisk.org/2011/05/02/tutorial-fixing-the-boot-loader-with-rescatux/)

It should do exactly what you need.

Larry

How does that work? Can I get it on my USB? I was thinking of putting ubuntu on my Usb and run these commands
 sudo apt-get install lilo sudo lilo -M /dev/sda mbr


I am a Linux noon I need steps. Thanks

---

### Post by lkraemer on 2012-08-10
[Introduction!]("http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html")

How does that work?
> 
Main Purposes of Super Grub Disk

    * To make life easier for new GNU/Linux users.
    * To educate people in how to use GRUB. This is why each option has its own explanation.

[Can I get it on my USB?]("http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html#Super_Grub_USB_Disk")
[Situations where Super Grub Disk is useful.]("http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html#situtions_where_sgd_is_useful")

> Super Grub Disk can also write other bootloader codes to MBR for you, from the operating system of your choice. For example, you can even restore the Windows bootloader code to MBR if you want to uninstall your Gnu/Linux operating system.


[URL="http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html"]
Bookmark it![/URL]



Larry

---

### Post by drmrgd on 2012-08-10
If I'm not mistaken, I believe you can repair the Windows bootloader by booting from the Windows 7 installation CD, and choose the Boot Repair option (or something like that - I can't quite remember the exact term).  I believe this will trash the current bootloader and set it up such that the system will only boot Windows.

---

