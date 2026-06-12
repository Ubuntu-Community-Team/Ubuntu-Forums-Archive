---
title: "Desktop Install on Dapper"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by designwebs on 2006-09-01
I'm at my witts end.  I have been over the IRC channell trying to get help.  Total waist of time.  Anyways when I try to install the desktop under the dapper drake server I get the following errors at the end.
[17:10] <John[1]> Now it says failed to fetch archive [http://us.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.07-0ubuntu5_i386.deb](http://us.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.07-0ubuntu5_i386.deb) Size mismatch.[17:12] <John[1]> The it says-E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing

What am I doing wrong?  I have run every command I can think of to no avail.

---

### Post by enopepsoo on 2006-09-01
I am sure some internet genius will come along an save the day shortly, but my advice is install xubuntu.  It seems to get on from a server install quite well.

Unless you are a die hard Gnome Baker like me.  In that case, wait for the internet genius.:D

---

### Post by designwebs on 2006-09-01
I guess what get me is you start asking questions and someone starts helping you and the they stop and ignor you like they never said anyhting to start with

---

### Post by blackened on 2006-09-01
If they're anything like I was when I used IRC alot, then they are also doing about 50 different things other than looking at IRC, and will often forget they are even connected. I would get absent-minded and accidentally leave in the middle of a conversation with someone.

We're all just human, with attention-spans to match sometimes.

Anyway, on topic again:
I assume you're using the command
```
sudo apt-get install ubuntu-desktop
```
?

---

### Post by kerry_s on 2006-09-01
Did you activate all your repos(sudo nano /etc/apt/sources.list)  uncomment(#)  to activate then> sudo  apt-get update <then> sudo apt-get install (x-window-system-core xterm fluxbox gdm synaptic <for fluxbox).

you can do "sudo su" to become root then you don't have to keep typing sudo. make sure you reboot after install just type "reboot".

if you keep getting failed try taking the "us." part out in the sources.list.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse 

to

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

---

### Post by blackened on 2006-09-01
I don't think that'll work kerry_s. I tried it both ways. This package seems to have gone missing from the repos or something.

Best I can suggest, designwebs, is that you download the package from the bottom of [this]("http://packages.ubuntu.com/dapper/libs/libsexy2") page (for your specific architecture), and install it with dpkg, then try ubuntu-desktop install again.

Edit: I guess I misread your post kerry_s. I think you just have the repo address wrong designweb. Try changing sources.list as kerry_s suggested, then try the ubuntu-desktop install again.

---

### Post by designwebs on 2006-09-01
> **kerry_s said:**
> Did you activate all your repos(sudo nano /etc/apt/sources.list)  uncomment(#)  to activate then> sudo  apt-get update <then> sudo apt-get install (x-window-system-core xterm fluxbox gdm synaptic <for fluxbox).

you can do "sudo su" to become root then you don't have to keep typing sudo. make sure you reboot after install just type "reboot".

if you keep getting failed try taking the "us." part out in the sources.list.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse 

to

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

I cannot thnak you enough!!! Your tips got me going.  I'm now up and running with the desktop gui on my LAMP Server.  Thanks you agian.

---

