---
title: "offline update ubuntu 10.10 to ubuntu 11.04"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by tanmoykrthakur on 2011-05-01
i want to update ubuntu 10.10 to ubuntu 11.04, due to slow internet i download  ubuntu-11.04-alternate-i386.iso for off line update but update process give this error "Could not download the upgrades.
The upgrade has aborted. Please check your Internet connection or
installation media and try again. All files downloaded so far are
kept.". please help me

---

### Post by codeninja1 on 2011-05-03
# Same problem here with upbgrade of 2.6.35-29-generic. Tried to mount and install from the alternate disk iso using:
sudo mount -t iso9660 -o loop /home/username/ubuntu-11.04-alternate-i386.iso /cdrom
then
sudo /cdrom/cdromupgrade
And got the same "abort" message you got.

---

### Post by -Rif- on 2011-05-08
this problem has been solved?
whats the solution? I'm having the same problem

---

### Post by kmkmahesh on 2011-05-09
i just burned the alternate image on cd, after inserting the cd i got a pop up message, 

when i selected "Run update" it failed so many times

i selected "Start Package Manager" works perfectly

---

