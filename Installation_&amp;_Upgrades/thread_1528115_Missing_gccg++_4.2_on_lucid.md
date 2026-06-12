---
title: "Missing gcc/g++ 4.2 on lucid"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by realn on 2010-07-10
Hi,

The title says it all. There are gcc 4.1 4.3 and 4.4 in the repositories, but the 4.2 is missing. And I need this one.
 Can someone please help me install it on LL ?

---

### Post by realn on 2010-07-20
Solved - fallback to Kubuntu Hardy Heron waiting for a real LTS release.

---

### Post by stewchang on 2011-02-14
Hi, apologies for the noob question, but can you elaborate on your answer? I'm also in need of g++-4.2 on Lucid. How does one add a repository for Kubuntu Hardy on Lucid? Thanks!

---

### Post by stewchang on 2011-02-14
Oh wait, got it. For other noobs, I had to:

(1) Open Synaptic Package Manager (System... Administration... Synaptic Package Manager)

(2) Open Repositories (Settings... Repositories)

(3) Add the Hardy Heron repositories (Other Software... Add... deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted)

(4) Uncheck all the previously checked repositories (under Ubuntu Software and Other Software)

(5) Close Repositories (Close... Reload)

(6) The list of available packages should now display g++-4.2 which you can select and install.

---

