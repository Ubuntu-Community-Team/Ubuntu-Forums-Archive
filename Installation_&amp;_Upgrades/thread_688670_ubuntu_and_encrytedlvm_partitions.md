---
title: "ubuntu and encryted/lvm partitions"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by jarthel on 2008-02-05
I've been installing ubuntu 7.10 using the alternate CD for several times now. 

It seems to me that when reinstalling the OS, I seem to lost the LVM/crypto definitions.

Is this correct? If yes, is there a way to retain it when I reinstall the Ubuntu? I know I do not have to reinstall in most cases BUT I think it's best to know my options. :)

Thank you :)

---

### Post by markitect on 2008-02-06
I've had problems with the installer not recognizing them too.  My solution is to use a regular partition for / and just my /home partition is lvm. 

When I reinstall I don't add a home partition, and then once it finishes I clear out the home directory and change fstab to mount the lvm partition there.

---

