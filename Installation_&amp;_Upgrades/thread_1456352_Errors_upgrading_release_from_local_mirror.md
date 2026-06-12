---
title: "Errors upgrading release from local mirror"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by baleks on 2010-04-17
Release upgrade ends up with error "Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

The server may be overloaded 


Restoring original system state" 
when doing do-release-upgrade -d to upgrade from karmik to lucid.
i using local mirror [ftp://ubuntu.snacho.ru](ftp://ubuntu.snacho.ru) (also have http that works but not browseable) 
when i change lines in /etc/apt/sources.list from local mirror to official [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) all works fine.

I don't want to download 1Gb from internet (becouse of traffic cost). What is wrong with local mirror ? I can communicate with its owner, but what he needs to change on the mirror ?

p.s. he mirrors from mirror.yandex.ru/ubuntu

---

### Post by baleks on 2010-04-18
maybe i should report a bug to do-release-upgrade application or some other package ?

---

