---
title: "Repositories down..."
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by flamer on 2007-10-18
I can't connect to: 

archive.ubuntu.com (91.189.88.43) 
 
It just hangs. Is it Down?

---

### Post by ezphilosophy on 2007-10-18
Exact same problem here in China.

---

### Post by jso2897 on 2007-10-18
My download ground to a halt a few minutes ago. i've tried a couple of different mirrors, but I'm getting nothing.

---

### Post by Steveway on 2007-10-18
Well, you should expect this to happen.
A wonder that this site still runs pretty stable today.

---

### Post by chispix on 2007-10-18
Same here - I'm seemingly stuck in the install phase at the moment. :(

The *'Installing System'* box reads "Configuring APT" and has been stuck at 82% for the last hour, with only the status of *'Scanning the mirror...'*

Might there be anything I can do to push it past that point? I really don't want to cancel out of the install if I don't have to.

Any help is greatly appreciated! :D

---

### Post by ezphilosophy on 2007-10-18
Yeah, it could be the traffic, but I'm not so sure.  I'm using the cn.archive.ubuntu.com.  Despite the number of people in China, I don't think there are THAT many people using the China servers now (it's 4:00 am).  There could be though...

---

### Post by honeydew on 2007-10-18
> **chispix said:**
> Same here - I'm seemingly stuck in the install phase at the moment. :(

The *'Installing System'* box reads "Configuring APT" and has been stuck at 82% for the last hour, with only the status of *'Scanning the mirror...'*

Might there be anything I can do to push it past that point? I really don't want to cancel out of the install if I don't have to.

Any help is greatly appreciated! :D


well I was having the same issue just a little while ago.. I did ctrl+alt+F2 to get to a console.. then did    
```
ps aux|grep apt
```
that gave me a list of apt processes running... I forget what the exact PID I ended but I had to try a few to get it it right.. I think it was one running as apt-setup or something or other..    the PID is the numbers that are listed on the far left.  
use:
```
kill PID#
```
  after you end it you can see if it effected the install by going back to ctrl+alt+F1 ... if you see a bright red screen thats good.. youll get a couple errors and then it gives you the option to skip that step.   I am now booted into my fresh ubuntu machine... afterwards you have to go correct your /etc/apt/sources.list and do a apt-get upgrade... 

hope this helps =]

PS::  Also.. I should of mentioned.. the whole ctrl+alt+F2/F1 thing is only necessary for alternate and server installs you should be able to achieve the same effect by opening a regular ubuntu terminal and typing sudo su to get into a root shell..

good luck..

---

### Post by chispix on 2007-10-18
> **honeydew said:**
> well I was having the same issue just a little while ago.. I did ctrl+alt+F2 to get to a console...
A *very* sincere 'Thank You' to you, Honeydew - I learn something new & feel more empowered with this OS every day because of friendly, patient people like yourself.

I'm now booted into my fresh installation of Gutsy Gibbon, and am excited to get started and learn more, and perhaps share the knowledge I obtain with others as considerately as you have for me.

Thanks again!! :D

---

### Post by steveneddy on 2007-10-18
I've tried to get some things off of Synaptic today and if it wasn't extremely slow, it wouldn't connect at all. I'll bet that the IT guys and gals at Ubuntu are having to learn things all over again. I'll bet that a couple of servers fried last night.

:popcorn:

---

### Post by lazka on 2007-10-18
> **chispix said:**
> Same here - I'm seemingly stuck in the install phase at the moment. :(

The *'Installing System'* box reads "Configuring APT" and has been stuck at 82% for the last hour, with only the status of *'Scanning the mirror...'*

Might there be anything I can do to push it past that point? I really don't want to cancel out of the install if I don't have to.

Any help is greatly appreciated! :D

[http://ubuntuforums.org/showthread.php?t=579920](http://ubuntuforums.org/showthread.php?t=579920)

---

### Post by bimmerd00d on 2007-10-18
the easynews repo is fast as can be :)....i'm only saying this b/c i've already downloaded my stuff :lolflag:

---

### Post by flamer on 2007-10-18
I've found a couple of mirrors

Go in software sources an change it to any of mirrors in the UK :)

---

### Post by honeydew on 2007-10-18
what are the easynews sources?  I have allways used archive.ubuntu.com would be sweet if there some other super highspeed ones I could get on..

---

