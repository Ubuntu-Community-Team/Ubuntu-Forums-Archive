---
title: "need to create a boot floppie to do a net install"
date: 2005-02-26
forum: Installation &amp; Upgrades
---

### Post by rolandhardwell on 2005-02-26
I have a HP netserver pro and no navigator cd. and the scsi cdrom is toast. can some one help me with the ingedients to make a netboot floppy =P~

---

### Post by bored2k on 2005-02-26
[QUOTE=rolandhardwell]I have a HP netserver pro and no navigator cd. and the scsi cdrom is toast. can some one help me with the ingedients to make a netboot floppy =P~[/QUOTE]

[Netboot Install](http://www.ubuntulinux.org/wiki/NetbootInstallHowto) 
[Smart Boot Manager](http://www.ubuntulinux.org/wiki/SmartBootManagerHowto) 

-----

Download debian bootable floppy images [easy thru the net ... deb is everywhere  :mrgreen: ]

> $ su
# dd if=<dir>/boot.img of=/dev/fd0
# dd if=<dir>/root.img of=/dev/fd0

---

