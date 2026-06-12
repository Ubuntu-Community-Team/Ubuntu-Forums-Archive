---
title: "hotkey-setup: 47: Syntax error:"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hobo on 2009-04-06
After downloading updates this AM I received this error. Could someone tell me what it means? Is it important?

This is the output after I did what Package Manager told me to do.

```
 hobo@hobo-laptop:~$ sudo dpkg --configure -a               
[sudo] password for hobo:
Setting up hotkey-setup (0.1-23ubuntu10) ...
/etc/init.d/hotkey-setup: 47: Syntax error: ";;" unexpected (expecting "fi")
invoke-rc.d: initscript hotkey-setup, action "start" failed.
dpkg: error processing hotkey-setup (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 hotkey-setup

hobo@hobo-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up hotkey-setup (0.1-23ubuntu10) ...
/etc/init.d/hotkey-setup: 47: Syntax error: ";;" unexpected (expecting "fi")
invoke-rc.d: initscript hotkey-setup, action "start" failed.
dpkg: error processing hotkey-setup (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:

```

hobo@hobo-laptop:~$ uname -a
Linux hobo-laptop 2.6.28-11-generic #40-Ubuntu SMP Fri Apr 3 17:39:51 UTC 2009 i686 GNU/Linux****

---

### Post by sasha0 on 2009-04-06
There is tiny error in /etc/init.d/hotkey-setup
If you add one "fi" (with no quotes) on line 46 of that file things should get better.

Broken code looks like this
```

    if laptop-detect; then

            do_video
    ;;

```  

and it should look like this

```

    if laptop-detect; then

            do_video
    **fi**
    ;;

```

---

### Post by Justin Trouble on 2009-04-06
[https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/356157](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/356157)

---

### Post by hobo on 2009-04-06
looks like this has already been reported to Launchpad and a patch to fix is available.

[https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/356157]("https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/356157")

---

### Post by hobo on 2009-04-06
That fixed it! Thanks for the fast response.

---

### Post by habtool on 2009-04-06
Thanks ;)

---

