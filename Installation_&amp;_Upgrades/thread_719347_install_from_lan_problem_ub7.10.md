---
title: "install from lan problem ub7.10"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by phneoix on 2008-03-09
hi,
i am trying to install ubuntu 7.10 on my toshiba portege 3110 (which does not have a cdrom or floppy drive) from lan. i have setup a pxe server and iam able to a netboot with the gutsy netboot image. 

my trouble start from here...  
i downloaded ubuntu alternate install cd and used the netboot files for tftp booting. it starts of well but comes to halt asking for mirror.

so i have downloaded whole mirror from archive.ubuntu.com using

-----------
 debmirror -v --host=archive.ubuntu.com --method=http --root=ubuntu --arch=i386 --dist=gutsy,gutsy-updates,gutsy-security --section=main,multiverse,restricted,universe --nosource --passive --ignore-release-gpg  /media/UAM/ubgutsy/
--------------

now when i point the installation to the mirror it says cannot find file. 
am i missing something. plz help.

---

### Post by banewman on 2008-03-09
I used the net install cd and had to point the installer to the us mirror for it to work.
:)

---

