---
title: "installing  ati drivers...x1800"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by enclo on 2009-11-22
hi  i'm  very  new to  ubuntu  and  could  use some  help ...
 can  get any  effect to  work do to no  ati  divers installed 
under  system/administration/ hardware driver it  show  nothing   empty box  bank 
 so  i  down load  .ati-driver-installer-9-3-x86.x86_64.run
opened terminal and  typed

  "sudo ./ati-driver-installer-9-3-x86.x86_64.run"
 i  typed this in in terminal and i  get  get  a Created directory fglrx-install.ew68J3
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593.....................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-14-generic; make sure that the version is being
correctly set by --iscurrentdistro

 how  can i  fix  this >?  clueless on what to  do next 
please help.... i know  nothing  about install stuff on  ubuntu ...

---

### Post by Mark Phelps on 2009-11-23
If harware drivers is empty, that's usually a good indication that there are no hardware drivers available.

ATI dropped support for lots of legacy cards back in May, their old drivers won't work with the Xorg in Ubuntu 9.04 or newer, their new driver won't work with the old cards.

Your best bet with a x1800 (no ATI drivers for this anymore) is to remove the restricted drivers and replace them with the open source drivers.  Instructions are in the link below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

