---
title: "duplicate sources"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by karrank% on 2008-08-07
Dumped Hardy and reinstalled Dapper, and may have accidentally ticked the wrong boxes trying to enable repositories and got this:

W: Duplicate sources.list entry cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dapper/main Packages (/var/lib/apt/lists/Ubuntu%206.06.1%20%5fDapper%20Drake%5f%20-%20Release%20i386%20(20060807.1)_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dapper/restricted Packages (/var/lib/apt/lists/Ubuntu%206.06.1%20%5fDapper%20Drake%5f%20-%20Release%20i386%20(20060807.1)_dists_dapper_restricted_binary-i386_Packages)




What, if anything, should I do here?

---

### Post by fluteflute on 2008-08-07
You need to edit your sources list. 

Press "Alt+F2" and enter the following:```
gksu gedit /etc/apt/sources.list
```
A long(ish) document will open (after you enter your password).

If you want to be able to install some new programs from the cd (normally if you have a slow internet connection) remove one line that includes 'cdrom' (leaving another).

If you would prefer to retain the ability to install programs from the cd (it can be annoying having to find the cd - especially if your internet connection is fast), remove all lines including 'cdrom'.

If you are not confident you may wish to 'comment out' the lines by prefixing them with a '#' rather than deleting them.

---

### Post by karrank% on 2008-08-07
> **fluteflute said:**
> You need to edit your sources list. 

Press "Alt+F2" and enter the following:```
gksu gedit /etc/apt/sources.list
```
A long(ish) document will open (after you enter your password).

If you want to be able to install some new programs from the cd (normally if you have a slow internet connection) remove one line that includes 'cdrom' (leaving another).

If you would prefer to retain the ability to install programs from the cd (it can be annoying having to find the cd - especially if your internet connection is fast), remove all lines including 'cdrom'.

If you are not confident you may wish to 'comment out' the lines by prefixing them with a '#' rather than deleting them.

definitely not confident! :D In fact I was wondering if anything needs to be done about it at all, and if so, why.

---

