---
title: "Help Just installed but wouldnt work"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by igoclimbingnaked on 2007-07-13
I Completely installed Ubuntu and i had no problem with that....but when i went to run it the first time it would load to the 3rd bar and just stop...any ideas?

---

### Post by Pumalite on 2007-07-13
Could you please post your specs?. Are you using Live CD? Alternate? Are you dual booting?

---

### Post by igoclimbingnaked on 2007-07-13
Im dual booting with windows xp and im using the alternate disc for version 7. whatever.

Like the ubuntu loading bar comes up and it gets to three bars and just stops.

---

### Post by Pumalite on 2007-07-13
Motherboard? Chipset? Graphics Card?IDE drive? SATA drive? Or a mixture of both? One drive, 2, 3?
Are you planning to give an entire drive to Ubuntu? Are you partitioning one drive?

---

### Post by igoclimbingnaked on 2007-07-13
Its an intel pentium 4, with an nvidea geforce 4mx 4000, and its just one 40gb harddrive for both os. I partioned the drives and the dual boot seems to work but when i select ubuntu it freezez when it gets to the third bar.

---

### Post by Pumalite on 2007-07-13
XP? Vista? How much memory?

---

### Post by igoclimbingnaked on 2007-07-13
windows xp and i have like 700 something mb of ram

---

### Post by Pumalite on 2007-07-13
Defrag XP several times, erase all temp files, get rid of anything you don't need. Then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) Create your partition and install with alternate CD. Check your iso ( Md5sum ) Check your cd for corruption, then install.

---

### Post by igoclimbingnaked on 2007-07-13
i had just reformated my harddrive so theres nothing to clean up and i partioned with the alternate disc or whatever...

---

### Post by Pumalite on 2007-07-13
Did you do checksum on your iso? Did you check your CD for corruption before install?

---

### Post by igoclimbingnaked on 2007-07-16
i have no idea what the first thing is but i did check the cd for corruption and there was none

---

### Post by Pumalite on 2007-07-16
A checksum ( Md5sum ) is something you can do with an utility of the same name. k3b in Linux does a checksum before burning. You need to compare that to  the Md5sum posted in the site ( Ubuntu org as an example ). If it matches, then you are good to go and burn. Burn at 4x or less. In general, for problematic installations, is better to go with the Alternate CD. Avoids graphical interface problems and sometimes other hardware quirks.

---

