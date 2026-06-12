---
title: "change cd-rom source in synaptic?"
date: 2005-07-04
forum: Installation &amp; Upgrades
---

### Post by smarttaz on 2005-07-04
I'm having /dev/cdrom as a DVD-ROM and /dev/cdrecorder as a CD-RW unit.
I installed Hoary from /dev/cdrom (which is a DVD) and now I can NOT change the CD-source to the other device, /dev/cdrecorder.

I even tried wuth apt-cdrom, but whatever I try to set up, it will always ask to insert the CD-ROM into the first device, not the second.

Any idea?

Thx.,
Radu-Cristian

---

### Post by Lunde on 2005-07-04
[QUOTE=smarttaz]I'm having /dev/cdrom as a DVD-ROM and /dev/cdrecorder as a CD-RW unit.
I installed Hoary from /dev/cdrom (which is a DVD) and now I can NOT change the CD-source to the other device, /dev/cdrecorder.

I even tried wuth apt-cdrom, but whatever I try to set up, it will always ask to insert the CD-ROM into the first device, not the second.

Any idea?

Thx.,
Radu-Cristian[/QUOTE]
 Use a .iso as the repsitory:
[http://www.ubuntuforums.org/showthread.php?t=35807](http://www.ubuntuforums.org/showthread.php?t=35807)

---

### Post by cotcot on 2005-07-04
Maybe change master/slave to slave/master (jumper on the back of the cdrom and cdrecorder)

---

### Post by smarttaz on 2005-07-04
[QUOTE=cotcot]Maybe change master/slave to slave/master (jumper on the back of the cdrom and cdrecorder)[/QUOTE]
NOOO! I mean, that synaptic (or aptitude, if any) would be able to ask or accept the CD-ROM in the other unit!
However, it seems that id there is a /dev/cdrom, it will not look for another one (e.g. /dev/cdwriter), if the installation was made from this one!
Tried to change in sources.list from "cdrom:" to "cdwriter:" -- zilch.
Tried to add a CD-ROM repository with "apt-cdrom" and specifying the device -- nada.
How in the **** manages SuSE's YaST to accept any CD unit?

---

