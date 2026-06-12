---
title: "Major aptitude problem"
date: 2008-09-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rocknrolf77 on 2008-09-30
Have a major problem with aptitude. Installed packagekit to check how it worked with ubuntu. Don't know if it has something to do with the problem. But anyway, I get this output when trying to install something :

```
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: parse error, in file `/var/lib/dpkg/available' near line 8856 package `hunspell-en-us':
 field name `' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/available' near line 8856 package `hunspell-en-us':
 field name `' must be followed by colon
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

```

Never encountered something like this earlier so anyone who has an idea how to fix this?

---

### Post by ronacc on 2008-09-30
there do seem to be some problems with packagekit , see this thread .
[http://ubuntuforums.org/showthread.php?t=909054&highlight=packagekit](http://ubuntuforums.org/showthread.php?t=909054&highlight=packagekit)
try to purge the pakagekit you installed .

---

### Post by mc4100 on 2008-09-30
If I remember correctly, there's a file "available-old" in:
```
/var/lib/dpkg/
```
Backing-up the file "available", deleting the original in /var/lib/dpkg, and then renaming "available-old" should fix your problem, however, **I suggest you do some research beforehand** as this could have unknown side-effects (ie., it might break things later, when that backup will come in handy).

---

### Post by rocknrolf77 on 2008-10-02
Chickened out and did a reinstall. It was a pretty fresh install anyhow so. And I had to use the laptop.

---

