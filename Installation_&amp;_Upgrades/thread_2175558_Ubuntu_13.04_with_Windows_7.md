---
title: "Ubuntu 13.04 with Windows 7"
date: 2013-09-19
forum: Installation &amp; Upgrades
---

### Post by steffes-jesse on 2013-09-19
I have Ubuntu 13.04 installed on my PC and I'm planning to install Windows 7 OEM I would like it to be in a dual boot setup. I heard that its for a clean install so will it try to remove my Ubuntu? Also any tips on setting up the dual boot (Like setting up the boot loader) would be appreciated.

---

### Post by Frogs Hair on 2013-09-19
Installing Windows before Ubuntu usually works better , but you certainly can do it. There maybe some boot loader or grub issues to resolve. Most tutorials you will find are for Windows before Ubuntu.     

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by su:bhatta on 2013-09-20
This Program called EasyBCD can be used in Windows to generate a new entry for Ubuntu if you have installed Windows after Ubuntu! 

[http://en.wikipedia.org/wiki/EasyBCD](http://en.wikipedia.org/wiki/EasyBCD)

I have done it once last May, and it was fairly easy to use and there were no complications. it found my Ubuntu and Elementary OS installations and resulting Boot screen was beautiful looking too :)

This page from developers website actually gives the details pretty well : [https://neosmart.net/wiki/easybcd/dual-boot/linux/ubuntu/](https://neosmart.net/wiki/easybcd/dual-boot/linux/ubuntu/)

---

### Post by mastablasta on 2013-09-20
all the tools you need are provided by ubuntu.
you need to install windows 7 then you need to repair grub (you can do it via command lin or use this:[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair))

---

### Post by steffes-jesse on 2013-09-22
Would it be best to backup my Ubuntu before hand just to be safe and if so what utility/method should I use.

Thanks for the help!

---

### Post by oldfred on 2013-09-22
In this case a full image may be best.
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
      
 Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

But I prefer to just backup /home, possibly some hardware configurations I manual made that are in /etc and possibly other special software like sql db that may not be in /home. And a list of installed applications. Then I can just do a new install with my old /home data and reinstall missing apps easily.

      
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

 Other applications if data not separate
apache, any sqldb, tomcat, web folders, etc
      
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[URL="http://ubuntuforums.org/showthread.php?t=1883834"]http://ubuntuforums.org/showthread.php?t=1883834
[/URL]
 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

[URL="http://ubuntuforums.org/showthread.php?t=1883834"]
[/URL]

---

### Post by alejandr on 2013-09-22
I think it's better to have  windowsinstalled before ubuntu.
then you can customize grub to choose deffault OS and timeout.
Ubuntu takes a lot of care handling HDD patitions and existing data than windows 7
you could lost your data inside HDD if you are not carefull installing windows over ubuntu.
I have this same config:
Dell Vostro 3300 laptop Windows 7 Pro, and Ubuntu 13.04 alongside with windows.
No problems so far.

I had Ubuntu LTS 12.04 installed by Wibu before, and I installed 13.04 and then uninstalled 12.04 from wubi uninstall.
I think Ubuntu is much more prepared to coexist with another OS than windows, and that's the reason i think is beter installing Windows 7 before ubuntu in a dual OS system

---

### Post by mastablasta on 2013-09-23
Clonezilla is a powerfull tool and really does need a tutorial with all it's switches and such. 

i found RedoBackup to be much simpler and easier to use (also used parted) and doesn't need a tutorial.

---

### Post by martinr on 2013-11-09
When you've installed Windoze and are about to install Ubuntu, just make sure that you don't boot the installation CD with a UEFI boot sequence if your HD structures is MSDOS with MBR or vice versa.
(See: [this thread]("http://ubuntuforums.org/showthread.php?p=12030957#post12030957"))

---

