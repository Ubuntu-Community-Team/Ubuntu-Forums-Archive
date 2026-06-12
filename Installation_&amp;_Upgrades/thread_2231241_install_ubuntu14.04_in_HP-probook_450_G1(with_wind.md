---
title: "install ubuntu14.04 in HP-probook 450 G1(with windows 7) errors"
date: 2014-06-24
forum: Installation &amp; Upgrades
---

### Post by kinggong88 on 2014-06-24
Hi all,
I just installed Ubuntu14.04 desktop version in my hp-probook 450 G1 (pre-installed with windows 7 professional SP1), it got some errors:
After I selected Ubuntu operating system, and hited *ubuntu menu, the screen occured the error messages below
   Serious errors were found while checking the disk drive for /.
   press I to ignore, S to skip mounting, or M for manual recovery

After I pressed I and S, it showed up the login screen, then I input ID/password, it poped up a few of messages below
   Welcome to Ubuntu 14.04 LTS (GNU/Linux 3.13.0-24-generic x86_64)
   .........
   .........
   then error messages follow
   /usr/lib/update-notifier/update-motd-update-available 39: cannot create /var/lib/update-notifier/updates-available: Read-only file system
   ........
   ........
   ........

What was worst, at home directory, I try to edit a file via vi, it said : unable to open swap file for "sample.txt", recovery impossible

I searched it on google, seems I need to change something inside the file /boot/grub/grub.cfg ! at this point, I can not open this file to write for changes even I tried using sudo vi ! What should I do ? please give some instructions to fix those errors, Thank you thank you so much !

---

### Post by Frogs Hair on 2014-06-24
Hello and Welcome

Did you partition the drive as a traditional dual boot or try and use the unsupported Windows (Wubi.exe)?

---

### Post by kinggong88 on 2014-06-24
Ah ! I used wubi.exe from the DVD I created (ubuntu-14.04-desktop-amd64.iso).

I cannot click on wubi.exe inside the DVD to start installing. I started wubi.exe under Dos console, it extracted files from the DVD. what wrong with that ? Thanks a lot !

---

### Post by Frogs Hair on 2014-06-24
Since Wubi is not supported there is no way to trouble shoot the latest version.  The 12.04 version of Wubi may work because it was supported when 12.04 was released. Keep in mind it is only for trial use and not for long term installation. 

[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

---

### Post by kinggong88 on 2014-06-24
Now I have a DVD of ubuntu14.04-amd64. What is the right way to install it in my laptop ? I am a newbie to linux, could you show me a step-by-step to direct my installation ? Thank you very much !!!

---

### Post by Frogs Hair on 2014-06-24
How the computer is partitioned by the manufacturer and whether it has secure boot affects how the installation is done. I can supply some links to look over . Please try booting from the dvd after removing wubi and be patient before trying to start the installation. Above all, post questions as needed. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


Edit: Boot from DVD [http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by kinggong88 on 2014-06-24
OK ! Let me try. Thanks a lot !!!

---

### Post by oldfred on 2014-06-25
Also if an HP with Windows 7, it probably was installed in BIOS mode with all 4 primary MBR(msdos) partitions used.

You have to free up one primary partition to allow it to be converted to an extended partition which is a container for as many logical partitions as you may want or need. Linux works just fine from Logical partitions. Windows has to boot from a primary.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by hakuna_matata on 2014-06-25
> **Frogs Hair said:**
> Since Wubi is not supported there is no way to trouble shoot the latest version.
There are some workarounds: [http://ubuntuforums.org/showthread.php?t=2217829](http://ubuntuforums.org/showthread.php?t=2217829) 
 
But if you can avoid Wubi, it is a better solution.

---

