---
title: "must manually run 'dpkg --configure -a' to correct"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by a7xmcrused on 2008-10-05
Im not sure what went wrong but as i was installing programs from the add/remove programs list in Ubuntu a message popped up saying

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

and now i cant install anything. any help would be appreciated.

---

### Post by Pumalite on 2008-10-05
sudo dpkg --configure -a

---

### Post by tuxxy on 2008-10-05
Open a terminal and enter the following command

```
sudo dpkg --configure -a
```

---

### Post by a7xmcrused on 2008-10-05
Thank you guys lol. i really should have thought of doing that...

---

### Post by Pumalite on 2008-10-05
You might have to run:

```
sudo apt-get -f intall
```

After the first command

---

### Post by flxrover on 2008-11-05
> **Pumalite said:**
> sudo dpkg --configure -a

sorry I'm still nubie for ubuntu

after i do this command, the ubuntu continuing t install some pending
update, and the source of the update is not active....

How if i want to make that update process gone...
That really make me stuck when updating other application

Thanks

---

### Post by Pumalite on 2008-11-05
Post the output of the command I gave you
(Copy and paste here)

---

### Post by dmddinesh on 2009-01-10
i can not install any software using apt get. following error will display

apt-get: error while loading shared libraries: librpm-4.2.so: cannot open shared object file: No such file or directory

then i run dpkg --configure -a
and give following error
.................
dinesh@FVXPC02:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of apt:
 dpkg (1.14.20ubuntu6) breaks apt (<< 0.7.7) and is installed.
  Version of apt to be configured is 0.5.5cnc6-fr1.
dpkg: error processing apt (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apt
.....................
what should i do for this

---

