---
title: "Is this upgrade safe?"
date: 2010-01-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by KrazyPenguin on 2010-01-09
just@just-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  indicator-applet indicator-applet-session indicator-messages
  indicator-session ubuntu-desktop
The following packages will be upgraded:
  binutils libasound2-plugins libdbusmenu-glib0 libdbusmenu-gtk0
4 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 1,690kB of archives.
After this operation, 1,057kB disk space will be freed.
Do you want to continue [Y/n]?   

Thanks 
;-)

---

### Post by zika on 2010-01-09
> **KrazyPenguin said:**
> just@just-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  indicator-applet indicator-applet-session indicator-messages
  indicator-session ubuntu-desktop
The following packages will be upgraded:
  binutils libasound2-plugins libdbusmenu-glib0 libdbusmenu-gtk0
4 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 1,690kB of archives.
After this operation, 1,057kB disk space will be freed.
Do you want to continue [Y/n]?   

Thanks 
;-)It doesn't seem safe. Read sticky about upgrades. I wouldn't use dist-upgrade. I use aptitude and safe-upgrade. This is obviously a partial upgrade I would avoid. Just my .05$.

---

### Post by slakkie on 2010-01-09
I would wait a while if I was you.

And I agree with the poster above me. Use apt-get upgrade or aptitude safe-upgrade. I prefer the latter, but it's up to you.

---

### Post by jocko on 2010-01-09
> **KrazyPenguin said:**
> just@just-laptop:~$[COLOR=Red] sudo apt-get dist-upgrade[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  indicator-applet indicator-applet-session indicator-messages
  indicator-session [COLOR=Red]ubuntu-desktop[/COLOR]
The following packages will be upgraded:
  binutils libasound2-plugins libdbusmenu-glib0 libdbusmenu-gtk0
4 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 1,690kB of archives.
After this operation, 1,057kB disk space will be freed.
Do you want to continue [Y/n]?   

Thanks 
;-)
When an update wants to remove ubuntu-desktop, it's not one you want to apply. This happens because an update wants to replace or remove a package that is listed as a dependency for ubuntu-desktop. The ubuntu-desktop package will probably be updated soon to fix the changed dependency.

And: If you're not sure what upgrades are safe, don't use the dist-upgrade option for updating a development version. It is a lot safer to use the normal upgrade option and let it hold back upgrades which break the dependencies for other packages until those other packages are upgraded.

---

### Post by KrazyPenguin on 2010-01-09
K thanks

---

### Post by phillw on 2010-01-09
+1 to the above.. the stickie to read is --> [http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

Having nearly borked my system, I use System --> Administration --> Update Manager   This method specifically alerts you to partial updates, and gives you the option to cancel them, whilst accepting the fully released ones.

Regards,

Phill.

---

### Post by KrazyPenguin on 2010-01-09
Yep I waited and all FULL updates came through.
thanks

Is it me or is Lucid super stable for an alpha??

Had a couple of bugs so far using Ubuntu Software Center, Installation, and AWN ( i always have bugs with AWN but I tested it anyway).

No biggies!!!

;-)

---

### Post by phillw on 2010-01-09
> **KrazyPenguin said:**
> Yep I waited and all FULL updates came through.
thanks

Is it me or is Lucid super stable for an alpha??

Had a couple of bugs so far using Ubuntu Software Center, Installation, and AWN ( i always have bugs with AWN but I tested it anyway).

No biggies!!!

;-)


Shhh !!!! ;)

[http://ubuntuforums.org/showthread.php?t=1352578](http://ubuntuforums.org/showthread.php?t=1352578)

Different people are getting different mileage.

Phill.

---

