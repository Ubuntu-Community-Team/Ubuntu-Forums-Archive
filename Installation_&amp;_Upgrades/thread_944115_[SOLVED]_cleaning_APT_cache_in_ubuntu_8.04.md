---
title: "[SOLVED] cleaning APT cache in ubuntu 8.04"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2008-10-11
Hi all,

 recently i read in a book as follows
  
  cleaning APT cache
  
  edit /etc/apt/apt.conf.d/10periodic as follows
  
APT::Periodic::Download-Upgradeable-Packages "1"; 
APT::Periodic::AutocleanInterval "0";
APT::Archives::MaxAge "7";


buit in my  /etc/apt/apt.conf.d/10periodic file i am finding only these entries 

APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";

there is no APT::Archives::MaxAge "7"; should i add it ?

I use ubuntu 8.04

---

### Post by cariboo on 2008-10-11
Look in /etc/apt/apt.conf.d/20archive, that is where the

APT::Archives::MaxAge 30

directive is set

I'm using the Intrepid beta mine is set a 30.

Jim

---

