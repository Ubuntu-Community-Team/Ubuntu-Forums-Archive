---
title: "Jigdo files Broken"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by nemo33 on 2007-04-20
Trying to download ubuntu-7.04-alternate-i386.iso using Jigdo I found that the

ubuntu-7.04-alternate-i386.jigdo file contains dead links to two files :

u7fSmLn5P_eOh6R8AID5sw=Debian:pool/main/u/update-manager/update-manager-core_0.59.19_i386.deb
XetQyMnF7VhW8PTKHN6FUw=Debian:pool/main/u/update-manager/update-manager_0.59.19_all.deb

while in archive.ubuntu.com there are only newer files :

update-manager-core_0.59.20_i386.deb 
update-manager_0.59.20_all.deb 


Please can anybody correct the .jigdo file ?

Thanks:(

---

### Post by cjwatson on 2007-04-20
Thanks. This was reported by a few people, and I think I've fixed the .jigdo and .template files now so that they don't refer to the file that's no longer in the archive. Download them both again and give it another test?

---

### Post by nemo33 on 2007-04-23
Hi,

not only to bother around I have in the meantime successfully upgraded my laptop using the update manager. It worked flawlessly!!!:) 

I also tested the Jigdo dowload of ubuntu-7.04-alternate-i386.iso and confirm it OK now.

Many Thanks!

---

### Post by anco on 2008-03-24
I was trying to download hardy-alternate-i386 for testing purposes, but tried during 1 week three times with fresh .jigdo and .template files, but every time i get 19 file errors... one is below, on the server there is a newer file.


File in the template:
--12:08:02--  [http://archive.ubuntu.com/ubuntu/pool/main/s/seahorse/seahorse_2.22.0-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/seahorse/seahorse_2.22.0-0ubuntu1_i386.deb)
           => `hardy-alternate-i386.iso.tmpdir/archive.ubuntu.com/ubuntu/pool/main/s/seahorse/seahorse_2.22.0-0ubuntu1_i386.deb'
Réutilisation de la connexion existante vers archive.ubuntu.com:80.
requête HTTP transmise, en attente de la réponse... 404 Not Found
12:08:02 ERREUR 404: Not Found.

file on the server.
[http://archive.ubuntu.com/ubuntu/pool/main/s/seahorse/seahorse_2.22.0-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/seahorse/seahorse_2.22.0-0ubuntu2_i386.deb)

I hope somebody can fix it. I like the jigdo method when it works. I used it quite a bit last few months to keep testing the latest versions.

Thanks,

---

### Post by anco on 2008-03-24
Okay today the jigdo download worked again. New .jigdo and new .template for the fourth time in a week downloaded and today many files were new and yes I got right away a good iso

Thanks for uploading good .jigdo and .template files.

---

