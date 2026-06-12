---
title: "Unmet dependencies message when installing red5 [SOLVED]"
date: 2016-07-04
forum: Installation &amp; Upgrades
---

### Post by astarmathsandphysics on 2016-07-04
I tried to install red5 through software center but got this message:

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Clicking on details reveled 

 The following packages have unmet dependencies:

red5-server: Depends: adduser (>= 3.11) but 3.113+nmu3ubuntu3 is to be installed
             Depends: java6-runtime-headless but it is a virtual package
             Depends: libred5-java (= 1.0~svn4374-3) but 1.0~svn4374-3 is to be installed
             Depends: libtomcat6-java (>= 6.0.20-7) but 6.0.39-1 is to be installed

How can I instasll red5? I need it for videoconferencing.

---

### Post by astarmathsandphysics on 2016-07-04
Installed dependencies in terminal

---

