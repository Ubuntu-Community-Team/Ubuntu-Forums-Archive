---
title: "I need help uninstalling netbeans"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by Bigdog60 on 2007-05-30
I tried to install netbeans but it didnt install but I cant acess my package manager because it gives me this error:- E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. I have tried to hit return/enter and it doesnt work. Also I have hit the n butting and when I try to abort this is what I get can somone please help.



joharrou@Josh:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
joharrou@Josh:~$ sudo dpkg --configure -a
Setting up netbeans5.5 (5.5-0.59) ...

This package is an installer package, it does not actually contain the
NetBeans IDE. You will need to go download the IDE from:

From the NetBeans IDE 5.5 Download page:
[http://www.netbeans.info/downloads/all.php?b_id=2323](http://www.netbeans.info/downloads/all.php?b_id=2323)

Select the English(en) tgz Download Archive Distribution 82.8 MB
[http://www.netbeans.info/downloads/s...3710&lang_id=1](http://www.netbeans.info/downloads/s...3710&lang_id=1)

and place the file in /tmp (with root.root ownership) now.


[Press RETURN to try again, 'no' + RETURN to abort] nnnnn

This package is an installer package, it does not actually contain the
NetBeans IDE. You will need to go download the IDE from:

From the NetBeans IDE 5.5 Download page:
[http://www.netbeans.info/downloads/all.php?b_id=2323](http://www.netbeans.info/downloads/all.php?b_id=2323)

Select the English(en) tgz Download Archive Distribution 82.8 MB
[http://www.netbeans.info/downloads/s...3710&lang_id=1](http://www.netbeans.info/downloads/s...3710&lang_id=1)

and place the file in /tmp (with root.root ownership) now.


[Press RETURN to try again, 'no' + RETURN to abort] n
Abort installation of NetBeans IDE
dpkg: error processing netbeans5.5 (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
netbeans5.5
joharrou@Josh:~$

---

### Post by theorem_hunter on 2007-05-30
apt does not have the netbeans packages thats why it asks you do download them first.

you need to follow all those links & download all those packages.
i had the exact same problem & fixed it by following the links & downloading & following those instructions... netbeans works well... you dont really need to use atp to install netbeans, you can get everything from the netbeans website... 

if you want to uninstall netbeans use:
```

sudo apt-get remove netbeans

```

eclipse you can install using apt with out any problems, as well as downloading & installing form the web site...

i hope that helps

---

