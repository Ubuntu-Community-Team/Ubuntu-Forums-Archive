---
title: "Trouble with update manager....."
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by sgtpete on 2008-09-08
When i try to open update manager i get this message:
'E:Type '--17:11:21--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

---

### Post by Sef on 2008-09-08
Applications > Accessories > Terminal

Paste or type this code:

```
sudo apt-get update
```

Paste any more errors here, if any.

then

> cat /etc/apt/sources.list

Paste the results here.

---

### Post by sisco311 on 2008-09-08
and the output of:
```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by sgtpete on 2008-09-08
> **Sef said:**
> Applications > Accessories > Terminal

Paste or type this code:

```
sudo apt-get update
```

Paste any more errors here, if any:Got this error
E: Type '--17:11:21--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list


then



Paste the results here.
Got this error:bash: cat/etc/apt/sources.list: No such file or directory


After i put typed " cat /etc/apt/sources.list.d/medibuntu.list"
got this result:"--17:11:21--  [http://www.medibuntu.org/sources.list.s/hardy.list](http://www.medibuntu.org/sources.list.s/hardy.list)
           => `hardy.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
17:11:22 ERROR 404: Not Found."


A couple of days ago i tried to add medibuntu to my repositories to enable VLC......seems it bungled my repositories....

---

### Post by sisco311 on 2008-09-08
remove the medibuntu repo, update your system:
```
sudo rm /etc/apt/sources.list.d/medibuntu.list
``````

sudo apt-get update
```and follow [this tutorial]("https://help.ubuntu.com/community/Medibuntu") to add the medibuntu repo.

EDIT: _make sure you copy and paste the commands exactly_

---

### Post by sgtpete on 2008-09-09
Thanks a ton, worked like a charm.

---

### Post by sisco311 on 2008-09-09
Cool!
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thread Tools.**

---

### Post by anilatluri on 2008-11-19
But I get this:
"'E:Type '--2008-11-18' is not known on line 1 in source list /etc/apt/sources.list.d/mediubuntu.list, E:The list of sources could not be read.'  :confused:

What do you suggest?

---

