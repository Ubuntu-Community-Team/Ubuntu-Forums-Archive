---
title: "having trouble with md5sums"
date: 2005-07-06
forum: Installation &amp; Upgrades
---

### Post by nephish on 2005-07-06
hey there,
just installed ubuntu 5.04 (Hoary)
heres the deal, half of what i wanted to install messes things up in apt.
when i try to install a package with some dependencies (audacity, mplayer-386)
something in there has a bad md5sum and i cannot install much.

any ideas?

here is what is in the sources.list

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

i did the apt-get update, looked good. did the --fix-missing looked good
not helping though.

any takers?

---

### Post by PacketCollision on 2005-07-06
The same thing happened to me.  I have not found a solution yet, but I am working on it.

---

### Post by Seth on 2005-07-06
[QUOTE=PacketCollision]The same thing happened to me.  I have not found a solution yet, but I am working on it.[/QUOTE]
 It's an issue right now.

Solution: sudo gedit /etc/apt/sources.list and remove all the "us." pieces. Now you have a bunch of addresses that start with [http://archive](http://archive)...

---

### Post by PacketCollision on 2005-07-06
[QUOTE=Seth]It's an issue right now.

Solution: sudo gedit /etc/apt/sources.list and remove all the "us." pieces. Now you have a bunch of addresses that start with [http://archive](http://archive)...[/QUOTE]
 Thanks, I just found out about that.  It fixed things quite nicely.

---

### Post by nephish on 2005-07-06
[QUOTE=PacketCollision]Thanks, I just found out about that.  It fixed things quite nicely.[/QUOTE]
 thanks worked for me too.

---

### Post by GnomicGhost on 2005-07-07
[QUOTE=nephish]thanks worked for me too.[/QUOTE]

Sorry that didn't work for me.

I'm trying to install multimedia codecs as at [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)
sudo apt-get install gstreamer0.8-plugins - comes back at me with:
----------------------------
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/libsndfile1_1.0.10-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/libsndfile1_1.0.10-2_i386.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
----------------------------

I tried removing the 'us' archives but that gave me:
----------------------------
E: Couldn't find package libsndfile1
----------------------------

Please help.  I did this on another install 2 days ago and didn't have a problem.  Is this a new problem in the last 24hours?

Is there another repository I (we) can add to retrieve these files from?

Thanks for any help.
GG

---

### Post by acascianelli on 2005-07-07
[QUOTE=Seth]It's an issue right now.

Solution: sudo gedit /etc/apt/sources.list and remove all the "us." pieces. Now you have a bunch of addresses that start with [http://archive](http://archive)...[/QUOTE]
 Worked for me, Thx alot.

---

