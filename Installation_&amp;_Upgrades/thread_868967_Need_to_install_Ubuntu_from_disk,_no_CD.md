---
title: "Need to install Ubuntu from disk, no CD"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by burnettwkg on 2008-07-24
Does anyone know what I need to do to install Ubuntu from a hard disk? I have no bootable CD/can't mount or get to the CD ROM drive on a Fujitsu Lifebook. I also would like to install on a portable USB drive to boot from. Any ideas would be helpfull.
thx

---

### Post by dstew on 2008-07-24
If you already have an operating system on the computer you can install Ubuntu over the internet using [unetbootin]("http://unetbootin.sourceforge.net/").

---

### Post by sandysandy on 2008-07-24
have a look here

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

regards

---

### Post by burnettwkg on 2008-07-24
Thanks, I will try

---

### Post by jimv on 2008-07-24
Quick and dirty USB installation:

1.  Get Ubuntu Desktop ISO
2.  Format thumbdrive as FAT
3.  Extract the contents of the ISO onto the thumdrive
4.  Install SysLinux with 'sudo apt-get install syslinux' or download the Windows executable from the Syslinux site
5.  Run Syslinux on your thumbdrive.  In Ubuntu, type 'sudo syslinux /dev/yourthumbdrive.  In Windows, open a cmd window, navigate to where you put syslinux.exe, and type 'syslinux.exe E:' or whatever drive letter your thumbdrive is.
6.  Open the thumbdrive and rename the isolinux folder to syslinux.  Open the syslinux folder and rename isolinux.cfg to syslinux.cfg.

7.  Attempt booting from the thumbdrive.

---

