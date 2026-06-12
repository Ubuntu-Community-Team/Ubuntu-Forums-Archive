---
title: "chroot trouble (i think)"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by MyKal on 2007-12-28
ok i had some trouble installing kubuntu from the minimal install cd in expert mode 

everything went well untill i reached the point where i had to select the packages i wanted to install 

i chose kubuntu-desktop and hit enter and it began downloading the selected packages but very quickly failed so i tryed again and the same thing happened only right away this time i tryed again a few times before finally admiting defeat at wich point i went to the next step wich was to creat a chroot however this step asked me again to first install my packages wich had allready been established wasnt going to work so i skipped ahead yet again and clicked finish wich ended me up with a working command line base environment from wich i was able to install a working kubuntu base system wich i am in right now 

the problem is that whenever i open dolphin i get an error saying that my bookmarks and configuration settings will not be saved do to the fact that i do not have proper permissions the exact error that i get is as follows:

Will not save configuration.
Configuration file "/home/lynn/.kde/share/config/d3lphinrc" not writable.
Please contact your system administrator.

and this:

Unable to save bookmarks in /home/lynn/.kde/share/apps/d3lphin/bookmarks.xml. Reported error was: Permission denied. This error message will only be shown once. The cause of the error needs to be fixed as quickly as possible, which is most likely a full hard drive

or when i try opening dolphin with the sudo command i get this in the terminal:

lynn@Lynn-Laptop:~$ sudo dolphin
[sudo] password for lynn:
Error: "/var/tmp/kdecache-lynn" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-lynn" is owned by uid 1000 instead of uid 0.


im pretty sure that these issues are due to the fact that i didnt set up the chroot durring the install processe and i am curiouse as to wether there is a way i can do this now after the fact or do i have to reinstall from the top

(let it be known that despite these permission problems everything seems to be working properly and i do have a working kubuntu kde desktop)

---

### Post by Pumalite on 2007-12-28
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://ubuntuforums.org/archive/index.php/t-579180.html](http://ubuntuforums.org/archive/index.php/t-579180.html)

---

### Post by MyKal on 2007-12-29
my uid is 1000 and i keep getting errors saying things cant happen because myuid is 1000 and not 0 if that helps any

---

### Post by Pumalite on 2007-12-29
[https://help.ubuntu.com/community/FilePermissions#head-70c5815728616c58f96152959e4d54ffd7aac0de](https://help.ubuntu.com/community/FilePermissions#head-70c5815728616c58f96152959e4d54ffd7aac0de)

---

