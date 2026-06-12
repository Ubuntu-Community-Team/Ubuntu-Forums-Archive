---
title: "pxe (with menu) localboot issues"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by surfer on 2010-08-30
i'm setting up a [FAI]("http://www.informatik.uni-koeln.de/fai/") server to be able to automatically install my bunch of clients. FAI can not only be used to install the clients but you can also just boot into a live system (with an ssh server) in order to fix problems.

what i'd like to do therefore is to set up my pxe boot server with a nice menu where i can choose at boot time whether i want to boot from the harddisk, install the system with FAI or boot into the live system. the latter two versions work nicely but i do not get the localboot version to work... if i use the simple file ( [FONT=Courier New]/srv/tftp/pxelinux.cfg/default[/FONT] )
```

default fai-generated

label fai-generated
localboot 0
append
```there are no problems. grub starts and everything is fine. but as soon as i try to use a menu around this like
```

default pxelinux.cfg/vesamenu.c32

prompt 0
timeout 120
ontimeout hd_boot

menu title PXE Boot Menu
menu width 80
menu rows  14
menu margin 10

label hd_boot
menu label ^Boot from local harddisk
localboot 0
append
```the localboot version does not work anymore... any ideas?

---

### Post by surfer on 2010-08-31
bump...

---

### Post by surfer on 2010-08-31
with some more googling i arrived at the conclusion that it's a syslinux (menu.c32/vesamenu.c32) issue. somehow the installed version is not compatible with the HP hardware i'm working on... nothing found so far. help still appreciated!

---

