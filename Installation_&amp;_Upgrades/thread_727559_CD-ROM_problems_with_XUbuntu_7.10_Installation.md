---
title: "CD-ROM problems with XUbuntu 7.10 Installation"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by dmartien on 2008-03-17
I am trying to install Xubuntu 7.10 on an older Toshiba Satellite 2500 CDT laptop with 192 MB of RAM and 20 GB hard drive. HDD and CD-ROM are IDE (could be EIDE; BIOS is not too specific).

I am using the text-based alternative CD.

The installation persistently fails during the "installing base system" portion due what the installer claims is a corrupted file on the CD-ROM drive. The file that fails is not consistent. Also, the CD verification reports corrupted files.

I know that the CD is ok, because I verified it in another computer.

Also, I am pretty sure that the computer's CD ROM drive is working fine. I can boot an Ubuntu 6.06 Live CD. It runs ok, although Gnome is really slow!

So, I am thinking that the kernel (or some kernel parameter) used by the 7.10 installer does not get along well with CD-ROM drive. Can anyone suggest a way to work around this?

Thanks for any help!

---

### Post by logos34 on 2008-03-17
Did you verify the checksum of the 7.10 .iso before you burned to cd?

---

### Post by dmartien on 2008-03-17
I did verify the md5 checksum of the iso. Good to check!

---

### Post by logos34 on 2008-03-18
Is windows installed, or is the hard disk blank?

---

### Post by dmartien on 2008-03-18
The hard disk previously had Ubuntu 6.06 installed. But it has since been repartitioned by the guided partition option of the installer. Do you think there might be a problem with the partitioning?

---

### Post by logos34 on 2008-03-18
no, I was going to suggest an installation straight from hard disk (i.e. ubuntu alternate .iso on the hard disk) [like this]("https://wiki.ubuntu.com/Installation/FromWindows") or [this]("https://help.ubuntulinux.org/community/Installation/FromLinux").  I thought maybe you could avoid the error that way.  But since you don't have a working OS on it, can't do it.

Strange.  The md5 is ok, cdintegrity check ok, you can boot and run live cd 6.06 but the installer complains about a corrupt file on cdrom.

---

### Post by logos34 on 2008-03-18
My only other thought is to try burning the iso again at a slower speed if possible, to make it easier for the cdrom to read it. Like 2x.

---

### Post by dmartien on 2008-03-20
Logos34, thanks for the last idea. I ended up burning the CD on a different computer. It seems that the Toshiba's CD-ROM drive doesn't like CDs burned in my Mac Book Pro. I got Xubuntu 7.10 successfully installed using a Live CD that I burned on another machine!

---

