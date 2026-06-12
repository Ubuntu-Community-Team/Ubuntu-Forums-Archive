---
title: "Has anyone got medibuntu repo working ?"
date: 2009-05-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-05-03
I've tried the various solutions previously posted for installing the medibuntu keyring but get the old problem that no pubkey is available. Has anyone got this working in karmic koala ?

---

### Post by taavikko on 2009-05-03
IIRC you don't need the key to be able to install packages from medibuntu.
Key is just used to offer guarantee that the repo is trusted, in a way...

Try to bear in mind that this is so early in the cycle that partners and such haven't yet adjusted to changes.

```
man apt-key
```
for that extra info on adding keys.

---

### Post by Kevbert on 2009-05-03
Thanks. I thought I might be jumping the gun a bit.:-({|=

---

### Post by jfernyhough on 2009-05-03
$ sudo aptitude install medibuntu-keyring
$ sudo aptitude update

Done. :)

---

### Post by Kevbert on 2009-05-03
> **jfernyhough said:**
> $ sudo aptitude install medibuntu-keyring
$ sudo aptitude update

Done. :)

No. This does not work for me. I'm connected to the main server (rather than my local GB one) and the medibuntu karmic repo is recognized in Synaptic/Software Sources. The output I get is:
```
kevin@kevin-dt2b:~$ sudo apt-get install medibuntu-keyring
[sudo] password for kevin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package medibuntu-keyring
kevin@kevin-dt2b:~$ sudo aptitude install medibuntu-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "medibuntu-keyring"
Couldn't find any package whose name or description matched "medibuntu-keyring"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
kevin@kevin-dt2b:~$ 
```

---

### Post by Nullack on 2009-05-03
why bother? what cant you do using ubuntu repos?

---

### Post by taavikko on 2009-05-03
> **Nullack said:**
> why bother? what cant you do using ubuntu repos?

There's not much point in using medibuntu.

w{32,64}codecs is obsolete, libdvdcss2 is available from install script provided by libdvdread4

Patched mplayer/mencoder, skype might be the only ones worth using...

---

### Post by scaine on 2009-05-03
Skype, Realplayer and Google Earth are all in Medibuntu.  And Adobe, if you use corporate PDFs that require the Adobe client.

---

### Post by autocrosser on 2009-05-03
The newest Adobe Reader is in the Canonical partner repos now--It's newer than the Medibuntu one & just a click away......

---

### Post by Kevbert on 2009-05-03
I'm having a problem with some DVDs and the problem occurs in both Karmic and Jaunty. See this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1147133"). I'm trying to attack it from two different angles...

---

### Post by Nullack on 2009-05-04
IMHO 3rd party repos are a potential security problem and a support nightmare

---

### Post by super.rad on 2009-05-04
I've never needed the medibuntu repo's and have videos, dvd's etc playing fine. They don't even have many packages in the repo (and i think most of them are in ubuntu anyway now) but they've added a karmic repo (although it's currently empty)

---

### Post by Kevbert on 2009-05-04
This is the first time I've had problems with DVDs, in most cases the ubuntu-restricted-extras package is enough. It's very strange that I can run the first and third parts of each B5 DVD but not the second.

---

