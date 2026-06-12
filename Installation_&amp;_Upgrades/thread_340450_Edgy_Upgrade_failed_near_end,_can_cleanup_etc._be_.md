---
title: "Edgy Upgrade failed near end, can cleanup etc. be run manualy"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by ftwig on 2007-01-17
I Have managed to upgrade to Edgy but just after the packages were fetched and installed the upgrade fell over.  I managed to complete the upgrade by doing 'apt-get -f install'.  Is there any way of manually starting the missing steps (i.e. clean up).  I have installed a few packages after the upgrade so this may cause a problem.

---

### Post by bapoumba on 2007-01-17
Hi,
what is the output to :
**cat /etc/apt/sources.list** 
**sudo apt-get update** or **sudo aptitude update**
**sudo apt-get dist-upgrade** or **sudo aptitude dist-upgrade**

---

### Post by ftwig on 2007-01-17
The apt-get bit all now works fine.  What I was asking is are there scripts I can run that will do the clean up etc.  Or possibly what exactly douse the cleanup do?

---

### Post by bapoumba on 2007-01-17
Sorry, I did read a little quickly :)
**sudo apt-get clean** or **sudo aptitude clean** (or **autoclean)** will clear up your cache and free some space.

For packages that you installed and do not need anymore, you'll have to uninstall them by hand (read man apt-get and man aptitude).

---

