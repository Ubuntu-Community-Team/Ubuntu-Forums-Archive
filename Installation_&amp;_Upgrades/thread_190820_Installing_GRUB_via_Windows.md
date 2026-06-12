---
title: "Installing GRUB via Windows"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by Cable on 2006-06-06
Is there a way to do this?  I used the GRUB Super Disk to boot into Windows (it couldn't fix my MBR for some reason).  So, I'm in Windows right now.  Please tell me there's a way to install GRUB from Windows...

---

### Post by Sutekh on 2006-06-07
Why not install GRUB using the LiveCD (Desktop CD) or Install CD (Aternate CD) following this link

[Ubuntu Wiki - Recovering GRUB After Installing Windows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows")

_________________________

I found these link on the Wiki page but I don't know much about them and one is pretty damn old. You could give it a shot, but I'd recommend the Wiki page instructions.

[GRUB4DOS and WINGRUB](http://grub4dos.sourceforge.net/)

[]("http://www.skyjammer.com/files/knoppix/")[Win32 Grub]("http://www.skyjammer.com/files/knoppix/")

[URL="http://www.geocities.com/lode_leroy/grubinstall/"] GRUB installer for windows (OLD)
[/URL]

---

### Post by missingxtension on 2006-10-02
w32grub.zip contains the GRUB boot loader. This is
necessary if you don't want to boot from floppy or
CD-ROM.

Just unzip it to c:\ then run c:\boot\grub\w32grub
This would patch the necessary files(under XP, not
linux). Then add :

c:\boot\stage1="GRUB" to c:\boot.ini

and you now have a grub boot loader on your XP system
which can be used to boot all flvors of linux. Check
the GRUB manual for detail how to add entries to GRUB.
source
[http://www.skyjammer.com/files/knoppix/](http://www.skyjammer.com/files/knoppix/)

---

### Post by missingxtension on 2006-10-02
<a href="http://www.skyjammer.com/files/knoppix/w32grub.zip">w32grub.zip</a> contains the GRUB boot loader. This is
necessary if you don't want to boot from floppy or
CD-ROM.

Just unzip it to c:\ then run c:\boot\grub\w32grub
This would patch the necessary files(under XP, not
linux). Then add :

c:\boot\stage1="GRUB" to c:\boot.ini

and you now have a grub boot loader on your XP system
which can be used to boot all flvors of linux. Check
the GRUB manual for detail how to add entries to GRUB.
source
[http://www.skyjammer.com/files/knoppix/](http://www.skyjammer.com/files/knoppix/)

---

### Post by randell6564 on 2006-10-02
Just boot into your Ubuntu CD, open up a terminal and type:

**sudo grub**

then type:

**find /boot/grub/stage1**

Whatever that returns, etc..(hd0) or (hd1),whatever,you will want to enter that with the next command.  So if it returns (hd0), then type:

**root (hd0,0)**

then type:

**setup (hd0)**

And finally type:

**quit**

This should install GRUB to your MBR and give you back your dual-boot option.

---

