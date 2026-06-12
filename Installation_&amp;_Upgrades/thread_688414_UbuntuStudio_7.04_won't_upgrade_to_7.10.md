---
title: "UbuntuStudio 7.04 won't upgrade to 7.10"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by Voltius on 2008-02-05
[SIZE="3"]=====VERSION INSTALLED=====[/SIZE]
Ubuntu Studio 7.04 installed and fully updated.
[SIZE="3"]
=====PROBLEM=====[/SIZE]
I'm trying to UPGRADE it to 7.10 through the Update Manager by clicking Upgrade where it says "new distribution release 7.10 is available ". It goes through the first part fine (donwloading files etc...) then it gets stuck on the 2nd step, (modifying repositories or something).
[SIZE="3"]
=====ERRORS GIVEN=====[/SIZE]
[COLOR="Red"]
Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg Could not resolve 'archive.ubuntustudio.org'
Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2 Could not resolve 'archive.ubuntustudio.org'
Failed to fetch http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz Could not resolve 'archive.ubuntustudio.org'
[/COLOR]

[SIZE="3"]=====MY PROFICIENCY IN LINUX=====[/SIZE]
I'm a n00b. Please be gently with me.

---

### Post by smartboyathome on 2008-02-05
I think that your problem is that Ubuntu Studio switched from their own repos to Ubuntu's. You may have to upgrade it manually.

---

