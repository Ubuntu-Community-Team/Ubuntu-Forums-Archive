---
title: "ubuntu broken...help!!!"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by windows-killer on 2008-11-10
Last week update manager brought me some new updates.
There was a font called ttf-leberation I install it without knowing what it was.
now when I try to update my computer, or when I install/ uninstall a program I always get this error:


                         An error occurred!

E: ttf-liberation: subprocess pre-removal script returned error exit status 1



EDIT: it always works when i install software but I get this annoying message. can someone help me?
I think I broke my computer!:lolflag:

---

### Post by windows-killer on 2008-11-10
anyone?

---

### Post by euxneks on 2008-11-10
have you tried (in a terminal):
```
sudo apt-get install ttf-liberation
```
and then 
```
sudo apt-get remove --purge ttf-liberation
```
The former installs again -- in case you're missing some files or scripts accidentally..
The latter removes completely the package -- **if** you want to remove it that is...

---

### Post by windows-killer on 2008-11-10
i typed the commands and heres what i got: 


After this operation, 1733kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122287 files and directories currently installed.)
Removing ttf-liberation ...
E: /var/lib/defoma/locked exists.
E: Another defoma process seems running, or you aren't root.
E: If you are root and defoma process isn't running undoubtedly,
E: it is possible that defoma might have aborted.
E: Please run defoma-reconfigure -f to fix its broken status.
dpkg: error processing ttf-liberation (--purge):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 ttf-liberation
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sukhhari on 2008-11-11
Else try with Ubuntu Recovery Mode, and select the options to fix the problems

1. Try cleaning for free space.
2. Fix the Problematic debian packages.

Try you luck.......:mad:

---

### Post by tommcd on 2008-11-11
> **windows-killer said:**
> 
E: Please run defoma-reconfigure -f to fix its broken status.


Try what APT is suggesting. Run:
```
sudo defoma-reconfigure -f
```
From "man defoma-reconfigure"
>   defoma-reconfigure reconfigures font configuration from zero.  It fixes
       a critical bug of data loss, but also is used  for  reconfiguration  of
       fonts.


EDIT: The command is defoma-reconfigure, not defoma. Post edited accordingly.

---

### Post by windows-killer on 2008-11-11
its still not working.:(:confused:
thanks for trying!:)

---

### Post by tommcd on 2008-11-12
If you can't uninstall it the way Euxneks suggested, and if **sudo defoma-reconfigure -f** did not work, then the only other thing I can think of is running:
```
sudo dpkg-reconfigure ttf-liberation
```
I have not been able to find any mention of this problem after searching the Ubuntu forums.

---

