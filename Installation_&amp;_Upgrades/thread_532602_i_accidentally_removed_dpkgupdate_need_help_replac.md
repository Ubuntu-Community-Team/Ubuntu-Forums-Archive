---
title: "i accidentally removed /dpkg/update/ need help replacing it"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by adom 00001 on 2007-08-22
i was trying to fix a problem with th update manager and i ended up removing /dpkg/update/ from my system, which only made the problem worse.  i now know how to fix my original problem but i cant really do anything with this computer until i figure out how to replace the file.  can anyone help me ??

---

### Post by PaulFr on 2007-08-23
What operating system version ? Are you sure it was /dpkg/update ? I see only > /var/lib/dpkg
/etc/dpkg
/usr/lib/dpkg
/usr/share/doc/dpkg
/usr/share/dpkgand only **/var/lib/dpkg/updates** which is not a file, but a directory.

---

### Post by adom 00001 on 2007-08-23
well i am using 7.04. 
and did i say file? i meant directory :P
you it all started when an installation crashed and i restarted my computer.  and the "dpkg --configure -a" was not working (i now know that i had to insert sudo for it to work) so i began trying to fix it others ways, and in that process i ended up removing /var/lib/dpkg/updates/

---

### Post by forestpixie on 2007-08-23
it's actually empty on mine - you could try making a new directory

sudo mkdir /var/lib/dpkg/updates/

---

### Post by adom 00001 on 2007-08-23
that did the trick, 
:)thnx

---

