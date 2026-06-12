---
title: "installing eggdrop *wont run*"
date: 2005-02-08
forum: Installation &amp; Upgrades
---

### Post by akurashy on 2005-02-08
have anyone installed eggdrop? well please explainme how to setup it because i have tried everything =/

it gives me this error

Eggdrop v1.6.17 (C) 1997 Robey Pointer (C) 2004 Eggheads
[23:23] * ERROR: Eggdrop will not run as root!


any ideas =/?

---

### Post by CrustyDOD on 2005-09-02
[QUOTE=akurashy]
[23:23] * ERROR: Eggdrop will not run as root!
[/QUOTE]
Read the error. Run it as normal user not root

---

### Post by veehell on 2005-12-21
[EggHelp]("http://www.egghelp.org/")
it might help you. There is complete step by step guide how to install from tared file via shell. 
Generally create user for your bot and run it as this user (not under your account) 

On ubuntu you need edit config file ( [SWAT's good hint ...]("http://www.ubuntuforums.org/showpost.php?p=393763&postcount=5") ) and also /etc/defaults/ check if there is(or is not) presented file for eggdrop (which denied to run eggdrop even if you have config) proftpd, firehol some stuff like that have those files to keep machine secure a point user to be carefull what he enable or run as service.
;) sometimes i forgot to edit those files to get my service up ;))
good luck.
PS: there are also some kind of "generating scripts" to prepare for you config file. But better to read examples and edit it.

---

