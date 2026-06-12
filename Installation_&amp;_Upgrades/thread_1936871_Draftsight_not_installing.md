---
title: "Draftsight not installing"
date: 2012-03-06
forum: Installation &amp; Upgrades
---

### Post by Mrenief78 on 2012-03-06
Hi,
 I've had DraftSight installed and it was working for a year.
I didn't renew the licence in time and I couldn't find out how to get it started again. 
So I just removed it and thought - well I'll just install it again from new..
Well... When I tried to install it - I get this message:
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 350976 files and directories currently installed.) 
Unpacking dassault-systemes-draftsight (from .../mike/Downloads/draftSight.deb) ... 
No protocol specified 
No protocol specified 
 
Gtk-WARNING **: cannot open display: :0.0 
dpkg: error processing /home/mike/Downloads/draftSight.deb (--install): 
 subprocess new pre-installation script returned error exit status 1 
Errors were encountered while processing: 
 /home/mike/Downloads/draftSight.deb 

any idea what the problem could be?
I am now on 12.04 but had the same problem last week when it was still 11.10.
Thanks,
Mike

---

### Post by Mrenief78 on 2012-03-06
Solved it using
sudo dpkg -i --force-architecture DraftSight.deb
in terminal

Note: I'm running ubuntu - not lubuntu that was my mistake when starting
the thread.
cheers.

---

### Post by achu91 on 2012-05-30
can u please list a detailed procedure on how to do it. i am using ubuntu 12.04 32 bit version. when i tried to do as per your instrction i gt the following error

[COLOR=Red]achu@Achuthan:~$ sudo dpkg -i --force-architecture DraftSight.deb
[sudo] password for achu: 
dpkg: error processing DraftSight.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 DraftSight.deb
[/COLOR]
pls do reply

---

### Post by ornerius on 2012-06-04
> **achu91 said:**
> can u please list a detailed procedure on how to do it. i am using ubuntu 12.04 32 bit version. when i tried to do as per your instrction i gt the following error

[COLOR=Red]achu@Achuthan:~$ sudo dpkg -i --force-architecture DraftSight.deb
[sudo] password for achu: 
dpkg: error processing DraftSight.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 DraftSight.deb
[/COLOR]
pls do reply

Two things:
1.) Linux is case sensitive, the package I download was named draftSight.deb
2.) Direct console the the correct path.
      In my case it was in my Downloads folder, off my Home folder, and to get there I typed: "cd Downloads" without quotes

then run the command as instructed... and remember case.

Note: Draft on my install of Ubuntu 12.04 has problems, namely the drawing space is always on top and obscures everything like the "save" dialog :/

---

### Post by achu91 on 2012-06-06
Finally i have installed the draftsight following your instructions.i don't face the face the problem as u have mentioned in the note and everything works well.
Thanks a lot for the help.

Achuthan.P

---

### Post by gmjsk on 2013-02-15
I did same thing and i got it

However, we have to install

libdirectfb-extra also from software centre

---

