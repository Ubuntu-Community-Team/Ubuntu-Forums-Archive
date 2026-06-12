---
title: "in windows install faILS"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Cool Surfer on 2008-04-24
```
could not access the cd, pl make sure another application is not using it and try again
```

i GET THE ABOVE ERROR AGAIN N AGAIN.

hOW TO FIX IT PL

---

### Post by Pumalite on 2008-04-24
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by rigo50 on 2008-04-24
The CD approach

This approach is documented in the Installation notes, however it seemed appropiate to put a reference to it here.

Note: This method only works with the Alternate Ubuntu install CD.

If you can't boot from the CD-ROM directly it is possible to use the above approach to boot the kernel from the HDD and have the installation follow through on the CD-ROM.

    *

      Create a directory called ubuntu in the root directory of the first primary partition of your hard drive (usually drive c:\, which it will be referred to as from now on).
    *

      Download the ALTERNATE ubuntu-installer CD from [WWW] [http://www.ubuntulinux.org/download/](http://www.ubuntulinux.org/download/) and burn the CD, then copy the contents of the CD to ubuntu.

Note: If you can't/don't want to burn a cd you can also mount the iso with a program like Daemon Tools or Alcohol 120%

    *

      Download Grub For Dos from [WWW] [http://sarovar.org/download.php/672/grub_for_dos-0.4.1pre22.tar.gz](http://sarovar.org/download.php/672/grub_for_dos-0.4.1pre22.tar.gz)

(this worked for me--current grub4dos available via [WWW] [http://sarovar.org/projects/grub4dos/](http://sarovar.org/projects/grub4dos/)

    *

      Extract grldr from the archive to c:\grldr. The rest of the files in the archive are unnecessary. (If your default compression/archive program doesn't like *.gz files, try 7-Zip from [WWW] [http://www.7-zip.org](http://www.7-zip.org).)
    *

      Append c:\grldr="Install Ubuntu" to c:\boot.ini.

To view and edit the Boot.ini file on WindowsXP:
1. Right-click on My Computer, and then click Properties.
2. On the Advanced tab, click Settings under Startup and Recovery.
3. Under System Startup, click Edit.

Note: Eventhough c:\boot.ini is not shown by the explorer, this file exists and can be also opened in the notepad. Just write the path c:\Boot.ini at the open dialog.

    *

      Create a new text file called menu.lst and save it to the first primary partition of your hard drive.
    *

      Open menu.lst in a text editor and paste the following text in the file:

      title Install Ubuntu
      kernel   (hd0,0)/ubuntu/install/vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
      initrd   (hd0,0)/ubuntu/install/initrd.gz

    *

      Save menu.lst, reboot with the Ubuntu installer CD in the drive, and select "Install Ubuntu" twice. You now have a CD installation of Ubuntu going.

---

### Post by Cool Surfer on 2008-04-25
Cant find instructions for 8.04

---

