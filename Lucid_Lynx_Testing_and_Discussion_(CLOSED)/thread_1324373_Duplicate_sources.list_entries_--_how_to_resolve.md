---
title: "Duplicate sources.list entries -- how to resolve ??"
date: 2009-11-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jerrynewt on 2009-11-12
Testing lucid on my HP Pavillion laptop (Triple boot -- ubuntu 9.10, kubuntu 9.10, and lucid) after installing Karmic and changing sources.list entries from karmic to lucid and updating and upgrading. Everything went good except terminal adivses me "Reading package lists... Done
W: Duplicate sources.list entry [http://76.73.4.58](http://76.73.4.58) lucid/main Packages (/var/lib/apt/lists/76.73.4.58_ubuntu_dists_lucid_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://76.73.4.58](http://76.73.4.58) lucid/universe Packages (/var/lib/apt/lists/76.73.4.58_ubuntu_dists_lucid_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://76.73.4.58](http://76.73.4.58) lucid/restricted Packages (/var/lib/apt/lists/76.73.4.58_ubuntu_dists_lucid_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://76.73.4.58](http://76.73.4.58) lucid/multiverse Packages (/var/lib/apt/lists/76.73.4.58_ubuntu_dists_lucid_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems".

I tried running apt-get update (sudo) a few times and same results. Looking at the sources.list file I can't find the duplicate entries. Do I need to be trying a different command to fix this ?? Thanks for the help

---

### Post by philinux on 2009-11-12
Have a look in here too.

/etc/apt/source.list.d

---

### Post by jerrynewt on 2009-11-12
Nothing in the sources.list.d file at all -- empty.

---

### Post by philinux on 2009-11-12
Change the server and try the update again then.

---

### Post by jerrynewt on 2009-11-12
Thank you sir -- worked like a charm !!

---

### Post by kio_http on 2009-11-12
When an issue is resolved click on thread tools > Mark thread as solved

---

### Post by Podex on 2009-11-12
> **jerrynewt said:**
> Nothing in the sources.list.d file at all -- empty.

Actually, sources.list.d is a directory in /etc/apt where third part repositories sources lists are stored.

---

