---
title: "I don't want automount in Ubuntu 10.04 ;( How?"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by super.kote on 2010-05-24
Hi, guys. 

I have a problem that I  can not decide for 2 weeks. 

**Here is what happened: **

On my laptop, installed  just Windows XP. In the past, when I  installed the second system, Ubuntu 9.04 or 9.10 (for dual-boot), Ubuntu  asked the administrator password for access to just Windows XP  partition. I mean, that just Windows  XP partitions were visible, but for the entrance (mount) needed a root  password. 

Now, in Ubuntu 10.04, Windows XP partition mount automatically and Ubuntu does not require  the root password. 

I do not like it very  much. [-X

Tell me please, what do  the settings at the time of installation of Ubuntu for just Windows XP  that the system would be asking root password for just Windows XP  partitions? 

Is this possible? I think - yes. Because in the past the  default 9.04 and 9.10 asked for a password. 


*PS: **I must say, as I put  Ubuntu and just Windows: *

1. Be installed just Windows  XP, giving it 20 GB space 100 GB hard drive. </span>The remaining 80  Gigabytes leave out the implications. 
 
2. Installed by Ubuntu for  free 80 gigabyte: 

a) 2 GB - swap 
b) 20 gigabytes - root  partition / 
a) 58 GB - home folder /  Home

All the settings, except  for manual partitioning, the default. 


Thank you.

---

### Post by dino99 on 2010-05-24
you have a nice tool to do that: install mountmanager to set your prefs about devices and partitions (system admin mountmanager)

[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

---

### Post by super.kote on 2010-05-24
> **dino99 said:**
> you have a nice tool to do that: install mountmanager to set your prefs about devices and partitions (system admin mountmanager)

[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

Thank you for your prompt  response. 

I installed this program,  but I do not know what line I should point mark, to request a password  for each entry in just Windows XP partitions. I am a beginner at  Ubuntu, tell me please what I need to mark? 

Please look at the  screenshot. Program has Russian  interface, but I think, visually, all standard and you can tell me. 

[IMG]http://static.itmages.ru/i/10/0524/h_1274705292_522407a6d9.jpg[/IMG]

Thank you 

Sorry for my English. But in the  Russian-speaking resource to me for 2 weeks, no one can tell the exact  answer: (

---

### Post by dino99 on 2010-05-24
wow its hard time for me too, english its ok but russian  :(

on your screenshot you have a line beginning with Kto ... with a scrolldown list choice: if you choose "administrator" then a password is requested, as you dont want to be asked about password, select "user"

you can press F1 for help too

---

### Post by super.kote on 2010-05-24
> **dino99 said:**
> wow its hard time for me too, english its ok but russian  :(

on your screenshot you have a line beginning with Kto ... with a scrolldown list choice: if you choose "administrator" then a password is requested, as you dont want to be asked about password, select "user"

you can press F1 for help too

Thank you for your patience :)

This line translate like: "Who can mount partition?" and answer: "Only administrator".

So, default settings is "Only administrator", BUT password is not requested :(

Why? :(

---

### Post by dino99 on 2010-05-24
[http://ubuntuforums.org/showthread.php?t=1403355](http://ubuntuforums.org/showthread.php?t=1403355)

---

### Post by alterpinguin on 2010-05-24
beside in older versions (i did not test this in 10.04) to disable the module for this, there is a way to disable it for nautilus.
nautilus is the "thing" in the default ubuntu installation and its settings can be changed with the "gconf-editor" in your user-settings.
start gconf-editor
-> apps
   -> nautilus
      -> preferences
and there are settings (with flag) for
media_automount     =should be for the mounting of (for example) inserted usb-sticks
media_automount_open =should be for the open/start of a new browser-window for this storage.

-
there is in: system->start-programs
additional entries for "informing about media-changes"
-
and last ooops,
if one dont want "automatic mounting" that is defined in /etc/fstab
one has to delete the lines there for this device. Then normaly
only root can do the mounting(and root has to know how, like dev-name and special codepages ...).

---

### Post by super.kote on 2010-05-24
> **dino99 said:**
> [http://ubuntuforums.org/showthread.php?t=1403355](http://ubuntuforums.org/showthread.php?t=1403355)

Sorry, but im not understand, how this can help me :(

---

### Post by super.kote on 2010-05-24
> **alterpinguin said:**
> beside in older versions (i did not test this in 10.04) to disable the module for this, there is a way to disable it for nautilus.
nautilus is the "thing" in the default ubuntu installation and its settings can be changed with the "gconf-editor" in your user-settings.
start gconf-editor
-> apps
   -> nautilus
      -> preferences
and there are settings (with flag) for
media_automount     =should be for the mounting of (for example) inserted usb-sticks
media_automount_open =should be for the open/start of a new browser-window for this storage.



I'm unmark "media_automount" and "media_automount_open", but system not requested the password and mount automatically :( Maybe i need restart system?

---

### Post by alterpinguin on 2010-05-24
> **super.kote said:**
> I'm unmark "media_automount" and "media_automount_open", but system not requested the password and mount automatically :( Maybe i need restart system?

sorry, was not clear explained by me,
those nautilus-options are for media-storage you insert after starting the computer like an usb-stick or a cd or dvd ...
all other storages, like the partitions on your running harddrive are normaly entries in /etc/fstab and if checked there for automount, then they are automounted.
If you have the "options" field for the storage (example /dev/sda3 or UUID=blablabla if the UUID is used) not set to "noauto"
like in /etc/fstab:
UUID=blablablablbl /media/sda3  ext3  rw,user,noauto   0
------------ check the noauto above----
then this storage will automatical be mounted.
Check: man fstab
for more information.
Either delete the whole line - or better mark it with "#" at the start
- or more better make a backup of the file ... and make the changes there.

---

### Post by super.kote on 2010-05-24
> **alterpinguin said:**
> sorry, was not clear explained by me,
those nautilus-options are for media-storage you insert after starting the computer like an usb-stick or a cd or dvd ...
all other storages, like the partitions on your running harddrive are normaly entries in /etc/fstab and if checked there for automount, then they are automounted.
If you have the "options" field for the storage (example /dev/sda3 or UUID=blablabla if the UUID is used) not set to "noauto"
like in /etc/fstab:
UUID=blablablablbl /media/sda3  ext3  rw,user,noauto   0
------------ check the noauto above----
then this storage will automatical be mounted.
Check: man fstab
for more information.
Either delete the whole line - or better mark it with "#" at the start
- or more better make a backup of the file ... and make the changes there.

Sorry, but in my file fstab i dont see Windows partition. Only this:

proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=c62af248-38e1-4dd0-a4b3-4930db409f33 /               ext4    errors=remount-ro 0       1
UUID=9924fb1b-7068-43ea-b451-c817edcd9aee /home           ext4    defaults        0       2
UUID=3fbe198e-66b8-4744-b5e6-2d26f8a8c6fc none            swap    sw              0       0

---

