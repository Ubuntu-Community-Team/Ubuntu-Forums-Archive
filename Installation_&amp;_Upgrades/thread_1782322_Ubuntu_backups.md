---
title: "Ubuntu backups"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by zanzibarwinds on 2011-06-14
Hi

Having installed Ubuntu 11.04 and installed various applications (LAMP server, Eclispe, Zend Studio, GIMP et. al.), done updates etc, is it possible to do a complete backup that would allow me to restore ubuntu in its current state (With all updates and installed apps etc) in some manner.

If possible installing/restoring the same "mirror" on a handy laptop I have laying about would be good although I'm guessing this wouldn't be possible due to hardware differences?

Cheers
John

---

### Post by mörgæs on 2011-06-14
Linux drivers are in the kernel (except closed-source drivers), so it is likely that it will work, if you don't need closed source drivers.

You could take a look at Clonezilla.

---

### Post by zanzibarwinds on 2011-06-14
Cheers I'll give that a look.

John

---

### Post by Maheriano on 2011-06-14
You could set up a RAID system so that your system would keep functioning if the state is lost. Or just look for something that creates a disk image, that's what you're looking for.

---

### Post by ezsit on 2011-06-14
Remastersys from [www.remastersys.com](www.remastersys.com) will allow you to create a live, bootable DVD backup of your system as long as the backup does not exceed 4GB.

---

