---
title: "help please - ktorrent 2.2.5"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by wnaBsd8d on 2008-01-27
hi everyone,

im having a problem installing ktorrent 2.2.5 on my ubuntu

at the moment im using 2.2.4 and its working fine  however i need to update for tracker reasons

moving on. when i try and compile the source code i get an error:

this error is during the ./configure

```
configure: error: libgmp is required to install this program
```

now ive looked everywhere for libgmp and have installed things that i assume are the same thing such as libgmp3c2 etc etc

now it would be a great help if anyone could direct me on how to install libgmp or if someone could complile me a deb package of ktorrent 2.2.5 or help in any way

thanks in advance

---

### Post by Pumalite on 2008-01-27
Do you have build-essential installed?

---

### Post by wnaBsd8d on 2008-01-27
> **Pumalite said:**
> Do you have build-essential installed?

yes i do version 11.3ubuntu1 is what it says in synaptic

---

### Post by Pumalite on 2008-01-27
Run:
sudo apt-get update
sudo apt-get upgrade
Post ant errors if any
If none, try to compile again.

---

### Post by wnaBsd8d on 2008-01-27
> **Pumalite said:**
> Run:
sudo apt-get update
sudo apt-get upgrade
Post ant errors if any
If none, try to compile again.

ok i ran both those commands and nothing seems to need updating and there where no errors

however when i compiled i still came up with the same error during the ./configure 

> configure: error: libgmp is required to install this program

any other ideas ?

---

### Post by p_quarles on 2008-01-27
```
sudo apt-get install libgmp3-dev
```

---

### Post by wnaBsd8d on 2008-01-27
thank you soo much you are amazing...it was right under my nose and i didnt even realise

thank you again

you sir are my hero

---

### Post by stoeptegel on 2008-01-28
> **wnaBsd8d said:**
> 
at the moment im using 2.2.4 and its working fine  however i need to update for tracker reasons


I am surprised that they pick up a new release this fast, i mean, KTorrent is just one day out.... I hope they don't expect packagers of distro's to be *that* fast. Anyway, glad you got it solved.

---

### Post by pt123 on 2008-02-01
Anyone know where to find a deb for 2.2.5

---

### Post by Tobi-fp on 2008-02-01
Hey there.. maybe you should try using "DELUGE", its a good torrent program which is a lot like Bitlord or azureus.. I prefer it.. If you woundlt like that, maybe you should try installing sudo apt-get install libgmp3-dev

---

### Post by bobby555 on 2008-02-01
Yea well I tried Deluge and it crashes constantly as well. Ktorrent seems to be a tad better, so I would like to try the new version asap.

AM

---

### Post by stoeptegel on 2008-02-01
2.2.5 still needs to be backported by jdong, i guess this will hapen soon... maybe a week or so.

---

### Post by pt123 on 2008-02-01
> **Tobi-fp said:**
> Hey there.. maybe you should try using "DELUGE", its a good torrent program which is a lot like Bitlord or azureus.. I prefer it.. If you woundlt like that, maybe you should try installing sudo apt-get install libgmp3-dev
I prefer a lot of the features in KTorrent. Deluge doesn't recognise any of the data you have already downloaded which you might have done using another client. There is also no way to manually ban peers (i.e. the ones that are not sharing).

---

### Post by stoeptegel on 2008-02-02
> **stoeptegel said:**
> 2.2.5 still needs to be backported by jdong, i guess this will hapen soon... maybe a week or so.

[https://bugs.launchpad.net/gutsy-backports/+bug/187374](https://bugs.launchpad.net/gutsy-backports/+bug/187374) (soon)

---

### Post by theTheme on 2008-02-19
I found this, it might be useful for you:

[http://www.orbitfiles.com/download/id2583114535.html](http://www.orbitfiles.com/download/id2583114535.html)

I'm installing now, let you know if it works

---

### Post by theTheme on 2008-02-19
Whenever I try to install I get this error:

```
(Reading database ... 114222 files and directories currently installed.)
Preparing to replace ktorrent 2.2.1-0ubuntu3 (using ktorrent_2.2.5.dfsg.1-2_i386.deb) ...
Unpacking replacement ktorrent ...
dpkg: dependency problems prevent configuration of ktorrent:
 ktorrent depends on kdelibs4c2a (>= 4:3.5.8-1); however:
  Version of kdelibs4c2a on system is 4:3.5.8-0ubuntu3.3.
 ktorrent depends on libgeoip1 (>= 1.3.17); however:
  Package libgeoip1 is not installed.
dpkg: error processing ktorrent (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ktorrent

```

---

### Post by pt123 on 2008-02-20
ktorrent should be available in the  repos. Try enabling more repos.

---

### Post by p_quarles on 2008-02-20
> **pt123 said:**
> ktorrent should be availlabe in the  repos. Try any enabling more repos.
This is true. Ktorrent 2.2.5 is now available in the Gutsy Backports repository. Enable that, and you can install it without any trouble.

---

