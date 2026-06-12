---
title: "GRUB problem with redhat 9.0 and ubuntu dapper"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by pradeepadapa on 2006-08-30
hi,

i hav first installed ubuntu dapper on an partition of 10GB on my hdd nd then i installed redhat9.0 in another partition of 10GB in the same hdd, but the problem is when the redhat GRUB loads i am only able to login into redhat but not ubuntu, i tried to reinstall the grub but to no avail. now i hav both ubuntu nd redhat in the same hdd but i m unable to login into only redhat but not ubuntu.

if anyone can giv the solution so that both the OS can be accessible through the same GRUB,plse mention the commands in detail to do it,bec i am an newbie.

:-k  :confused: :(

---

### Post by Vladimirm on 2006-08-30
Login to Ubuntu open a terminal and 

(as root)mkdir /media/redhat 

mount /dev/hda1(or whatever hardrive/partition Redhat is on)/media/redhat

vim /media/redhat/boot/grub/menu.lst

and copy and paste the entry for redhat into /boot/grub/menu.lst

Do this if you installed ubuntu after redhat

---

### Post by pradeepadapa on 2006-08-30
hi vladimirm,

glad to see ur reply, but shuld i login into ubuntu through live cd nd do the commands which u hav said through terminal, nd for ur understanding i hav installed redhat on ubuntu. nd how can i know on which partition is redhat linux swap or root present, when i see through partition magic from windows i see 2 swap partitions nd 2 EXT 3 partitions in the hdd.

plse help.

---

### Post by ajgreeny on 2006-08-30
Sorry Vladimirm, but pradeepadapa can't login to ubuntu if you note what he says.  What is needed is to login to redhat, mount the ubuntu partition and then copy the entries for ubuntu from the /boot/grub/menu.lst file to the redhat menu.lst file or grub.config file or whatever it is in redhat.

Once you have done that you can boot into ubuntu, and if you want to, put your ubuntu grub onto the hard disk instead of redhat, by typing:-
sudo grub-install /dev/hda  (you may need to change the /dev/hda to suit your machine.  You will then need to add the redhat grub entry to ubuntu as Vladimirm said to enable you to use the redhat OS.

I hope that all makes sense.  I have just told you to add a reverse of what Vladimirm told you and then do what he did, but you could just stop after the first bit if you want and use the redhat grub instead of ubuntu's.

---

### Post by Vladimirm on 2006-08-30
Can you install redhat onto an ubuntu partition and both of them still function?

---

