---
title: "Bootup Stalls at GRUB......"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by coldstream on 2006-06-04
I am Ubuntu newbie and decided to give it a try tonight after using Fedora for several years (FC5 lately) but after re-partitioning my SCSI drives (two) and installing the server version of Ubuntu, it went to reboot the machine after removing the installation CD.  Upon finishing the BIOs screen bootup, it immediatelys displays "GRUB" then space and the flashing cursor.  Then NOTHING.  It just sits there, no activity on the HDs either.  Anyone point me the direction where to look for possible issues?   Its late at night and I need to go to bed and hoping to see some helpful ideas in the morning so I can get the home machine up and running.  :-k

---

### Post by coldstream on 2006-06-05
Found that the MBR was set on the HD0 drive and not the SDA1 drive I intended.

---

