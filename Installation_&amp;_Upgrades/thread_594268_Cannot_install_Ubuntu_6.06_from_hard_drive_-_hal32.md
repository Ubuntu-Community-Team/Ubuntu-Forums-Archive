---
title: "Cannot install Ubuntu 6.06 from hard drive - hal32.dll error"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by HosBosCos on 2007-10-27
hi everyone,
i downloaded the Ubuntu 6.06 iso and  i don't have any cd-drive. so i tried to install from hard drive following these steps  [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows) (the ones at the bottom).

i did all the things and also downloaded right vmlinuz and initrd.gz i guess ( the ones here [http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/))

after rebooting the grub screen appears and i choose install ubuntu. But it says it cannot find the file [Windows Root]\system32\hal32.dll and restarts when i press any key.

so first of all why does it complain about something about windows? i'm trying to install ubuntu.
and how can i overcome this problem?

thanks in advance

---

### Post by It_Was_Luck on 2007-10-27
First off... Ubuntu 7.10 is out, so why are you trying to download 6.06...

Secondly... Have you checked you MBR (master boot record), Grub could be looking for ubuntu in the wrong place...

Thridly... Did you look over the files: 

Note: Eventhough c:\boot.ini is not shown by the explorer, this file exists and can be also opened in the notepad. Just write the path c:\Boot.ini at the open dialog.

    * Create a new text file called menu.lst and save it to the first primary partition of your hard drive.
    * Open menu.lst in a text editor and paste the following text in the file:

-------------------------------------------
      title Install Ubuntu
      kernel   (hd0,0)/hd-media/vmlinuz root=/dev/ram0 ramdisk_size=128000
      initrd   (hd0,0)/hd-media/initrd.gz
--------------------------------------------

    *Save menu.lst, reboot, select "Install Ubuntu" twice. You now have a CD image installation of Ubuntu going.


hth

---

### Post by HosBosCos on 2007-10-28
i'm installing 6.06 because my computer is a little bit old and i don't want it to run slow.

i also did all the things as it is written on this page [https://help.ubuntu.com/community/In...on/FromWindows](https://help.ubuntu.com/community/In...on/FromWindows)
i changed boot.ini and created menu.lst correctly.
and i placed the iso file under c:\
but after reboot when i choose install ubuntu, it gives an error about hal32.dll

has somebody an idea?

thanks.

---

