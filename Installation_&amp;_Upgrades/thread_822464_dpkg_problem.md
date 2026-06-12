---
title: "dpkg problem"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by charlesff on 2008-06-08
Hey everyone,
I install some new packages and when I tried opening Synaptic Package Manager and I got the following message:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```
After doing that I got:
```
dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 24 package `dmsetup':
 EOF after field name `'
```
What should I do?

---

### Post by Sef on 2008-06-08
Did you run ```
sudo dpkg --configure -a
```?

---

### Post by charlesff on 2008-06-08
> **Sef said:**
> Did you run ```
sudo dpkg --configure -a
```?

Yes that is the command I entered

---

### Post by meindian523 on 2008-06-08
now did you try again to see whether the problem has been solved?:lolflag:

EDIT: misunderstanding. ](*,)

---

### Post by charlesff on 2008-06-08
> **meindian523 said:**
> now did you try again to see whether the problem has been solved?:lolflag:

The problem is still there. I don't see the red sign at the top of my screen but when I open Synaptic Package Manager I get the same error message.

---

### Post by meindian523 on 2008-06-08
and I believe you get the parse error even after running dpkg --configure -a
Are there any error messages when you run dpkg --configure -a?

---

### Post by meindian523 on 2008-06-08
and I'm sorry for that LOL sign.I thought it's just another newbie not doing what's put in front of him/her.

---

### Post by charlesff on 2008-06-08
> **meindian523 said:**
> and I'm sorry for that LOL sign.I thought it's just another newbie not doing what's put in front of him/her.

It is Ok meindian523.
```
~$ sudo dpkg --configure -a
[sudo] password for *****: 
dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 24 package `dmsetup':
 EOF after field name `'
```
This the output when I enter sudo dpkg --configure -a.I only get a parse error.
and btw I am a linux newbie :D

---

### Post by meindian523 on 2008-06-08
This looks similar and it's been solved.Look :

[http://ubuntuforums.org/showthread.php?t=821235](http://ubuntuforums.org/showthread.php?t=821235)

---

### Post by meindian523 on 2008-06-08
It basically seems you have to delete the offending file(/var/lib/dpkg/updates/0000 in your case) and then run sudo apt-get update && sudo apt-get upgrade.

---

### Post by bapoumba on 2008-06-08
Please look [here]("http://ubuntuforums.org/showthread.php?t=385886"), post #5.

---

