---
title: "LVM devices not in /dev"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by speedway on 2007-03-08
Howdy

I have just installed 6.10 via the Alternate CD (command line install) and used apt-get to install lvm2. I was going so well until.....

My problem is that vgcreate is not putting the resulting group in the /dev/ directory, the only place I can find them is in /etc/lvm/backup. I checked lvm.conf and it says they should be created in /dev (and my desktop version of 6.10 puts them there ok) but they don't seem to be anywhere. I have checked for evms by looking for /dev/evms (and locate evms) but it does not appear to be installed. Oh, and I am logged in as root (sudo -i -H) and am not using sudo....

I am lost...can anyone suggest anything?

Cheers
Bruce

---

### Post by speedway on 2007-03-08
> **speedway said:**
> Howdy

I have just installed 6.10 via the Alternate CD (command line install) and used apt-get to install lvm2. I was going so well until.....

My problem is that vgcreate is not putting the resulting group in the /dev/ directory, the only place I can find them is in /etc/lvm/backup. I checked lvm.conf and it says they should be created in /dev (and my desktop version of 6.10 puts them there ok) but they don't seem to be anywhere. I have checked for evms by looking for /dev/evms (and locate evms) but it does not appear to be installed. Oh, and I am logged in as root (sudo -i -H) and am not using sudo....

I am lost...can anyone suggest anything?

Cheers
Bruce
Forget this, I am tired. I forgot to do the bloody lvcreate bit....

Need sleep...

---

