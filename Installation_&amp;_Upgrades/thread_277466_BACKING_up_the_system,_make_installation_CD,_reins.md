---
title: "BACKING up the system, make installation CD, reinstall it"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by javb on 2006-10-14
Hi all,

i wonder, is there anyway i can get a totally/perfect copy of my now running machine on a CD? i mean, Make Ubuntu make an instalable ISO like the one we download from ubuntulinux.org but adding the prefs and softwares u have configured and installed with so much dedication?

Reason: I want to install Ubuntu on another laptop, same as mine, and i want to have everything the same, which is a lot (Softwares updates, instalation, configuration... bla bla bla, just imagine all those hours using apt-get install/upgrade/update/dist-upgrade)

There has to be a way to so ! 

Hope u can help guys !  ! !

---

### Post by Haegin on 2006-10-14
try partimage or copy the partition using gparted or pq magic

---

### Post by javb on 2006-10-14
copying the partition wont give an installable version of Ubuntu like mine. thats a robust way.  .  .

imagine i want to install the same system on a lab of 20 computers, the same...

Will i have to set everything up on each computer.. ? 

There has to be a way 

(i ` m still searching)

---

### Post by Haegin on 2006-10-14
You could use dpkg --set-selections and dpkg --get-selections so you perform a normal install on machine 1, install all the programs, get the selections, perform normal installs on the other machines and then use set selections to install all the programs onto the other machines to match the first. Of course you would still need to change any config files.
I was suggesting partimage or copying partitions so you could copy it to the other pcs once the first is set up rather than making an install cd. That would copy everything and would be fine for multiple identical machines.

---

### Post by javb on 2006-10-15
So it seems there is no software to do so, anyway thanks for your help  and your time.. i ll foruming.. ;)

Joel Valdez

---

