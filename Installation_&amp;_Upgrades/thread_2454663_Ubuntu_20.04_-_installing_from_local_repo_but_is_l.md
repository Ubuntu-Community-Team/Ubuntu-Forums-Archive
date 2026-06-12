---
title: "Ubuntu 20.04 - installing from local repo but is lookin for package that doesnt exist"
date: 2020-12-03
forum: Installation &amp; Upgrades
---

### Post by jpaquette77 on 2020-12-03
Hi,

Ive got a few mysteries that I cant seem to solve and they dont appear to be addressed in any documentation Ive come across. Was hoping someone can better my understanding of using a mirror repo.

Ive create a local mirror repo with apt-mirror and have been successfully installing Ubuntu 20 via PXE so my repo and config were good at one point, but recently, the installer started breaking at "Download installer components". Nothing has changed in my repo nor the apache server, etc. 

In /var/log/syslog:

Dec  3 23:02:05 anna[4469]: http://<myoscacheserver>:88/<myrepopath>/pool/main/d/debootstrap/debootstrap-udeb_1.0.118ubuntu1.2_all.udeb:
Dec  3 23:02:05 anna[4469]: 2020-12-03 23:02:05 ERROR 404: Not Found.
Dec  3 23:02:05 anna[4469]: WARNING **: package retrieval failed

I've confirmed my repo does not have this package, it has only:
debootstrap-udeb_1.0.118ubuntu1.3_all.udeb
-and-
debootstrap-udeb_1.0.118ubuntu1_all.udeb

So I have 1 and 1.3 but not 1.2, which doesnt seem to exist as I cant find it in any other archive. Google comes up with nothing useful.

What file is responsible for telling the installer what packages to install?

Ive checked all the "Packages" files but none point to debootstrap-udeb_1.0.118ubuntu1.2. So why is it asking for it? Why now when it was working before? and why cant I find that package anywhere?

Thanks!

---

