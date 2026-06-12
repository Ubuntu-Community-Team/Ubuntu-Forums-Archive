---
title: "Installing Ubunutu Without Cd-Rom"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by RussellGee on 2007-09-08
My friend gave me an old pc he had and asked me if I could get xubuntu working on it, the problem is it had no cd-rom or usb bios support.

First I made a new partiton and created a folder called /boot then I downloaded the 6.10 alternative iso and the initrd.gz and vmlinux files.From the ubunutu ftp.Then I intalled grub4dos, edited the boot.ini and created a menu.lst file.

The installer started and everything went well untill it got to the stage where it searched for the iso file which it said it couldnt find.

Anybody got any ideas how to fix this?

-RussellGee
__________________

---

### Post by Sef on 2007-09-08
Is the computer a [desktop]("https://help.ubuntu.com/community/Installation/Netboot?highlight=%28Install%29") or [laptop]("https://help.ubuntu.com/community/Installation/HardDriveAndPcmcia")?

---

### Post by RussellGee on 2007-09-08
Its a desktop

I have tryed the netboot install and it never worked.

I know it is possible doing it this way as I know people who have done it.

-RussellGee

---

### Post by Pumalite on 2007-09-08
Is this what you tried?:[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by pxwpxw on 2007-09-08
Also note there was a bug in the 610 hd-media (iso install method ) that caused the iso not found problem,  this is fixed in feisty704. The net install was always ok . (not netboot, just a simple install from net mirrors , using downloaded install vmlinuz and initrd. )

---

### Post by logos34 on 2007-09-08
I think you want to go with a network installation/net install.  Try  [UNetbootin]("http://lubi.sourceforge.net/unetbootin.html").  It's the easiest.

-->[unetbootin-ubuntu704rev21.exe]("http://sourceforge.net/project/showfiles.php?group_id=198821")

---

### Post by iheartubuntu on 2007-09-08
> **logos34 said:**
> I think you want to go with a network installation/net install.  Try  [UNetbootin]("http://lubi.sourceforge.net/unetbootin.html").  It's the easiest.

-->[unetbootin-ubuntu704rev21.exe]("http://sourceforge.net/project/showfiles.php?group_id=198821")

Thanks for this info! This might actually help out my problem since my cdrom drive on my old laptop doesnt seem to work for booting up.

---

