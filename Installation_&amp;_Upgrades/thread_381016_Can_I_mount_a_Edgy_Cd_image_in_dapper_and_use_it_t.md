---
title: "Can I mount a Edgy Cd image in dapper and use it to upgrade ?"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by roon on 2007-03-10
Hi,
   
    I want to upgrade Dapper to edgy. I have got a Edgy alternate install image. Can I use it to upgrade my Dapper to edgy without burning it to a CD ? If yes then how ?

Plz answer.

---

### Post by roon on 2007-03-10
solved it:

I upgraded my ubuntu using the following steps :

1. First I entered this command to mount the Cd image in the /media/cdrom directory **sudo mount -t iso9660 /home/my_user_name/ubuntu-6.10-alternate-i386.iso /media/cdrom -o loop**


2. Then I entered this command **gksu "sh /cdrom/cdromupgrade"** and it upgraded my Dapper to Edgy.

---

