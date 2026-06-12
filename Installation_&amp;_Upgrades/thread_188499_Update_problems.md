---
title: "Update problems"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by geir2rs1 on 2006-06-04
Hi,
I tried to update my Breezy installation this morning prior to upgrade to Dapper.  I ran into this problem after the update claimed it had completed sucessfully. 

When I try to start Update Manager it pops up telleing me it is analysing the system, but after a few seconds it just dies and disapear without any messages or anything.

I tried to open Synaptic and it gave me this message:

E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.

I then tried to run sudo apt-get "update" from a command line. It gave me the same  message.

Can anyone please help me?

Geir

---

### Post by majed on 2006-06-04
try changing the sources.list file then try synaptic.. 

use this: [http://www.ubuntuforums.org/showthread.php?t=185758]("http://www.ubuntuforums.org/showthread.php?t=185758")

Good luck!

---

### Post by ubuntu_demon on 2006-06-04
Please read this thread prior to upgrading / installing Dapper :
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

You should use this **clean Dapper sources.list :**

[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

---

### Post by ubuntu_demon on 2006-06-04
[QUOTE=majed]try changing the sources.list file then try synaptic.. 

use this: [http://www.ubuntuforums.org/showthread.php?t=185758]("http://www.ubuntuforums.org/showthread.php?t=185758")

Good luck![/QUOTE]

Please advice people to use this sources.list instead : [http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

During dist-upgrading from Breezy to Dapper non-official repos should be commented. Dist-upgrading using the update-manager tool is easy as it comments all non-official repo's automatically.

I have commented the cipherfunk repository for now in my "recommended Dapper sources.list" because apparently people are using it to upgrade from Breezy to Dapper(this will prevent issues). Although the post clearly says :

> 
If you are still using breezy then you should** upgrade to Dapper first before using this sources.list**. You should take a look here prior to upgrading :
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)


After a couple of days I will uncomment the cipherfunk repository again.

---

