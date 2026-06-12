---
title: "Upgrade Problems"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by Leoq on 2010-03-07
So I am running ubuntu off a 4gb usb. It is set up so i can save and all that jazz. I have been trying to install the upgrades for a while now, and I can't seem to get access to the 'available' file. It says something about it being locked. And this makes it so I can't upgrade.

sudo apt-get update works fine. but sudo apt-get upgrade doesn't. I have also tried both from the root@ubuntu terminal.

Does anyone know what issue I am having? It seems like it's something simple.

---

### Post by MelDJ on 2010-03-07
could you post the output of sudo apt-get upgrade?

---

### Post by Leoq on 2010-03-07
Ok so here it is.

After a bunch of names of programs and stuff. It tells me 230 upgraded, 0 newly installed, 0 to remove and 13 not upgraded. 

then I hit 'y' to continue.

It extracts the template from packages to 100%
and preconfigures packages then it fails. heres what it says. 

dpkg: failed to open package into file `/var/lib/dpkg/available' for reading: input/output arror
dpkg: failed to open package into file `/var/lib/dpkg/available' for reading: input/output arror
touch: cannot touch `/var/lib/update-notifier/dpkg-run-stamp' : Input/output error
E: Sub-process /usr/bin/dpkg returned and error code (2)

Thats the error... I ran that one on Ubuntu@ubuntu:~$

--------------------------------------------------------------------------------------------------------------------

Edit*

So I have looked at both [This]("http://ubuntuforums.org/http//ubuntuforums.org/showthread.php?t=872210") post and [This ]("http://ubuntuforums.org/archive/index.php/t-389997.html")post... and none of these have worked for me :( Am I in big trouble?

---

### Post by MelDJ on 2010-03-07
try 

```
sudo dpkg --configure -a
```

and if it doesn't work

```
sudo apt-get install -f
```

---

### Post by Leoq on 2010-03-07
so the first didn't work same error as before, the second worked but said that 243 not upgraded. 

Should I try sudo apt-get upgrade now?

---

### Post by MelDJ on 2010-03-07
yes :)

---

### Post by Leoq on 2010-03-07
Sadly it's still not upgrading I tried it in the root@ubuntu also. 

I won't give me the access to the 'available' file I guess? is that a normal thing?

---

### Post by Leoq on 2010-03-07
Ok I just tried to remove totem with the synaptic package manager. And it didn't let me, exact same error as before. So I think there's something really wrong here.

---

### Post by Leoq on 2010-03-08
In addition I can no longer install anything....

Does anyone know what's wrong here?

---

