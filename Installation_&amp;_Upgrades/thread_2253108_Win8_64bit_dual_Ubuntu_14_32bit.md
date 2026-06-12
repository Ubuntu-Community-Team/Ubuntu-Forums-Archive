---
title: "Win8 64bit dual Ubuntu 14 32bit"
date: 2014-11-17
forum: Installation &amp; Upgrades
---

### Post by sasa3 on 2014-11-17
I got laptop with Win8 64bit and install linux and now i  cant acces to linux always go to Win8..I tried everthing..Tried boot repair but he said me that Uefi dont allow because 32bit Linux..can i upgrade bios or something?

---

### Post by Terry_Easler on 2014-11-17
Suggest you read this rather comprehensive reply to similar question.  Because of this info , I have not tried to install on my Win8.1 P.C.  [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

---

### Post by Impavidus on 2014-11-17
It's certainly possible to dual boot Win8 and Ubuntu. You will need the 64 bit version of Ubuntu though, but on hardware that has been designed for Win8 64 bit is best anyway. Have a look here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Although Ubuntu should work with secure boot on, there seems to be hardware around where this doesn't work. You can turn secure boot off. To allow Ubuntu to detect Windows, you have to turn fast boot off in Windows.

---

### Post by ajgreeny on 2014-11-17
If your Win8 is installed in UEFI mode, which is the default on just about all new machines, you must also install Ubuntu 64bit in UEFI mode as well.  There is no way that I'm aware of that you can change the installed version of Win8 from UEFI to MBR/legacy

Ubuntu 32 bit will not work, or is very difficult to get to work, in UEFI as far as I'm aware, so why bother trying.

HP and some others will not let you set anything other than Windows as default in UEFI menu. But there are work arounds.

UEFI still lets you boot devices and the /efi/Boot folder has  bootx64.efi which is the hard drive boot entry. If you rename that and  make it be grubx64.efi then booting hard drive boots grub menu.

Other work arounds.
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Script that automates the rename. Not tested but looks like it should work.
      
 script to auto create bootx64.efi as grub
[http://askubuntu.com/questions/54964...log-how-to-fix]("http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix")

---

### Post by oldfred on 2014-11-17
Also if reinstalling only use Something Else. That way you reuse the existing Linux partitions that are already created. 

And make sure you have made full backup of Windows and a Windows repair flash drive. Best to have those even if not making major changes to system, but whenever making major changes to systems you need good backups.

Note this bug on why you must use Something Else.
       Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions. Entire drive means everything.
Sept 2014 Fix being released for one drive installs, but mulitiple drive installs must use Something Else. And fix is not in current versions.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

