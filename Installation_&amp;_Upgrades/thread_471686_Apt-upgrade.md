---
title: "Apt-upgrade"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by idefixgallier on 2007-06-12
Hi!

I am new to Ubuntu (I used Suse Linux for years) so I have less experience with apt.
I installed a 7.04 server version and tried to update to the latest patches with the
following result - it is almost german, I translate the important parts below:

root@ubuntu:/opt/zope2.9.7/instance1/bin# sudo apt-get -V upgrade
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Die folgenden Pakete sind zurückgehalten worden:
   linux-image-server (2.6.20.15.14 => 2.6.20.16.28.1)
   linux-server (2.6.20.15.14 => 2.6.20.16.28.1)
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 2 nicht aktualisiert.

Apt says that it not upgraded 2 packages, linux-image-server and linux-server which I 
assume that they are the Kernel images - my question is, why does apt not upgrade those 2?

lg
Martin

---

### Post by bapoumba on 2007-06-12
What ubuntu flavor do you currently have (**lsb_release -cd**), and what kernel do you use (**uname -a**)?

---

### Post by idefixgallier on 2007-06-13
Hi!

lsb_release -cd:
Description:    Ubuntu 6.06.1 LTS
Codename:       dapper

uname -a:
Linux www3 2.6.15-26-server #1 SMP Fri Sep 8 21:00:37 UTC 2006 i686 GNU/Linux

lg
Martin

---

### Post by bapoumba on 2007-06-14
Did you try dist-upgrade ?

---

### Post by idefixgallier on 2007-06-14
Thank you very much, that solves the problem!

lg
Martin

---

### Post by bapoumba on 2007-06-14
You're welcome (and sorry for the late answer).

---

