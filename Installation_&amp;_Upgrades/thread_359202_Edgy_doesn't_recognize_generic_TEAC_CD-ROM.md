---
title: "Edgy doesn't recognize generic TEAC CD-ROM"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by clarkkent435 on 2007-02-11
Hate to post rather than lurk, but here goes...

Edgy (6.10) clean install from ISO-burned CD-ROM on a Dell Latitude X200 laptop. I get as far as CD detection before it tells me it can't find a CD-ROM drive; none of the recommended manual options work. It's a TEAC CD-224E 24X CD-ROM, nothing fancy.

Alt-F2 to shell, and there's nothing in /dev/cdrom; no luck finding a driver online to load by floppy.

Ideas? Thanks.

---

### Post by teaker1s on 2007-02-17
make sure it's not on cable select on jumper and possibly check if there is a firmware update from manufacturer of drive

welcome

---

### Post by cpet on 2007-04-06
' same problem  here with 'fiesty fawn' and 24x Pioneer  cd rom.

I changed jumper from 'cable select' to slave (bios didn't like 'master') as teaker1s suggests.

No luck, also tried bios settings for UDMA and power management.

---

### Post by cpet on 2007-04-24
Also tried A Nec of similar type and age as the Pioneer mentioned above. Feisty installed after using LG CD-WR
but still won't recognize the Pioneer cd-rom which is what I wish to leave in the system. Aparently i might type etc/fstab?

---

### Post by jmo8795 on 2007-06-26
This is a pretty old thread, so you've probably resolved this by now, however, just in case this might help...

I had the same problem trying to install 6.10 and 7.04 on a Dell X200 with the CD drive installed in a media base.  

I was able to get the installer to detect the drive by using the text based alternate install disc.  After the installer prompts you that it can't detect a CDROM it will ask you if you want to manually specify a location to find the drive. 

Input the drive location as /dev/scd0.  This fools the installer into thinking that the CD ROM is an external SCSI drive.

I'm guessing this would work with an external firewire or USB drive too.

Hopefully this will be helpful to someone.

---

