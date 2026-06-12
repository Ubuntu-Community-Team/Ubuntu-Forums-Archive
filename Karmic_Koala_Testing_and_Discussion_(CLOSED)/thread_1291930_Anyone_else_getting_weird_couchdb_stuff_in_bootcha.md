---
title: "Anyone else getting weird couchdb stuff in bootchart?"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-10-15
Not affecting boot time but I've not seen this in other peeps boot charts.

---

### Post by ronacc on 2009-10-15
got it here too , looking back at previous boots it seems to have started tuesday after an update .

---

### Post by philinux on 2009-10-15
Ok, I checked for bugs and I've raised one.

[https://bugs.launchpad.net/ubuntu/+source/couchdb/+bug/452143](https://bugs.launchpad.net/ubuntu/+source/couchdb/+bug/452143)

Could you confirm it please. Cheers.

---

### Post by ronacc on 2009-10-15
confirmed .

---

### Post by philinux on 2009-10-15
> **ronacc said:**
> confirmed .

Cheers, I'm interested what they will say about this.
I've seen other peeps bootcharts without it. Maybe 64 bit related.

---

### Post by jmmL on 2009-10-15
I get it and I'm on 32-bit.

---

### Post by castrojo on 2009-10-15
Couchdb is supposed to be there for desktop syncing for addressbooks and bookmarks. 

It affected my boot time before but I filed a bug about it (it was pulling in xulrunner) and that was fixed so it should affect not your boot time.

EDIT: Aha, got more info, can you make sure that couchdb is NOT installed and that couchdb-bin IS installed? There's an existing bug for this so I will dupe it when I find it.

---

### Post by benj1 on 2009-10-15
the couch db stuff has been added for backing up stuff to ubuntu one 
[http://lwn.net/Articles/356911/]("http://lwn.net/Articles/356911/")

---

### Post by philinux on 2009-10-15
> **whiprush said:**
> Couchdb is supposed to be there for desktop syncing for addressbooks and bookmarks. 

It affected my boot time before but I filed a bug about it (it was pulling in xulrunner) and that was fixed so it should affect not your boot time.

EDIT: Aha, got more info, can you make sure that couchdb is NOT installed and that couchdb-bin IS installed? There's an existing bug for this so I will dupe it when I find it.

Got both!

```

apt-cache policy couchdb
couchdb:
  Installed: 0.10.0-0ubuntu1
  Candidate: 0.10.0-0ubuntu1
  Version table:
 *** 0.10.0-0ubuntu1 0
        500 http://gb.archive.ubuntu.com karmic/universe Packages
        100 /var/lib/dpkg/status
philinux@philinux-karmic:~$ apt-cache policy couchdb-bin
couchdb-bin:
  Installed: 0.10.0-0ubuntu1
  Candidate: 0.10.0-0ubuntu1
  Version table:
 *** 0.10.0-0ubuntu1 0
        500 http://gb.archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status
```

```
sudo apt-get remove couchdb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  couchdb-bin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  couchdb
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 81.9kB disk space will be freed.
Do you want to continue [Y/n]?
```

---

### Post by philinux on 2009-10-15
> **benj1 said:**
> the couch db stuff has been added for backing up stuff to ubuntu one 
[http://lwn.net/Articles/356911/]("http://lwn.net/Articles/356911/")

Check out the bootchart in post one. Mutltiple entries.

---

### Post by castrojo on 2009-10-15
Ok remove the "couchdb" and rebootchart please!

---

### Post by ronacc on 2009-10-15
a little more checking of my boot charts and I found that this started for me on october 2 not 13 , after an update to couchdb-bin  to 0.10.0~svn818859-0ubuntu1 . not there before the update is there on the next boot .

---

### Post by philinux on 2009-10-15
> **whiprush said:**
> Ok remove the "couchdb" and rebootchart please!

I guess autoremove would get rid of couchdb-bin. How do you stop that?

Going for a reboot.

---

### Post by benj1 on 2009-10-15
> **philinux said:**
> Check out the bootchart in post one. Mutltiple entries.

sorry thought you were questioning why it was there at all

---

### Post by philinux on 2009-10-15
Ok couchdb removed but same thing in bootchart.

---

### Post by ronacc on 2009-10-15
removing couchdb and couchbd-BIN gets rid of it . also reduces boottime by 5 sec .

---

### Post by jmmL on 2009-10-15
Removing couchdb (but leaving -bin) solves this for me. I also experience the ~5s reduction in boot time.

Edit: I should also point out I disable ubuntu one from starting, if that's relevant.

---

### Post by castrojo on 2009-10-15
jmmL, Ok please add your comments and your boot charts (before and after) to the bug. ronnac if you could attach yours to the bug also that would help.

---

### Post by Longinus00 on 2009-10-15
If you want to see some funny stuff just search for couchdb processes.
```
$ ps aux | grep couchdb
couchdb   1348  0.0  0.0   1748   588 ?        S    17:17   0:00 /bin/sh -e /usr/bin/couchdb -a \"/etc/couchdb/default.ini\" -a \"/etc/couchdb/local.ini\" -b -r 5 -p /var/run/couchdb/couchdb.pid -o /dev/null -e /dev/null -R
dl        2481  0.0  0.0   1748   552 ?        S    17:18   0:00 /bin/sh -e /usr/bin/couchdb -n -a \"/etc/couchdb/default.ini\" -a \"/etc/xdg/desktop-couch/compulsory-auth.ini\" -a \"/home/dl/.config/desktop-couch/desktop-couchdb.ini\" -b -r 0 -p /home/dl/.cache/desktop-couch/desktop-couchdb.pid -o /home/dl/.cache/desktop-couch/desktop-couchdb.stdout -e /home/dl/.cache/desktop-couch/desktop-couchdb.stderr -R
dl        2508  0.0  0.0   1748   328 ?        S    17:18   0:00 /bin/sh -e /usr/bin/couchdb -n -a \"/etc/couchdb/default.ini\" -a \"/etc/xdg/desktop-couch/compulsory-auth.ini\" -a \"/home/dl/.config/desktop-couch/desktop-couchdb.ini\" -b -r 0 -p /home/dl/.cache/desktop-couch/desktop-couchdb.pid -o /home/dl/.cache/desktop-couch/desktop-couchdb.stdout -e /home/dl/.cache/desktop-couch/desktop-couchdb.stderr -R
dl        2509  0.0  0.7  62816  7884 ?        Sl   17:18   0:00 /usr/lib/erlang/erts-5.7.2/bin/beam.smp -Bd -K true -- -root /usr/lib/erlang -progname erl -- -home /home/dl -noshell -noinput -smp auto -sasl errlog_type error -pa /usr/lib/couchdb/erlang/lib/couch-0.10.0/ebin /usr/lib/couchdb/erlang/lib/mochiweb-r97/ebin /usr/lib/couchdb/erlang/lib/ibrowse-1.5.2/ebin /usr/lib/couchdb/erlang/lib/erlang-oauth/ebin -eval application:load(ibrowse) -eval application:load(oauth) -eval application:load(crypto) -eval application:load(couch) -eval crypto:start() -eval ssl:start() -eval ibrowse:start() -eval couch_server:start([ "/etc/couchdb/default.ini", "/etc/xdg/desktop-couch/compulsory-auth.ini", "/home/dl/.config/desktop-couch/desktop-couchdb.ini"]), receive done -> done end. -pidfile /home/dl/.cache/desktop-couch/desktop-couchdb.pid -heart
couchdb  10963  0.0  0.0   1660   544 ?        Ss   17:30   0:00 heart -pid 10954 -ht 11
couchdb  10971  0.0  0.0   2952   628 ?        S    17:30   0:00 sleep 5
couchdb  10972  0.0  0.0   1748   484 ?        S    17:30   0:00 sh -c /usr/bin/couchdb -k
couchdb  10973  0.0  0.0   1748   508 ?        S    17:30   0:00 /bin/sh -e /usr/bin/couchdb -k
couchdb  10974  0.0  0.0   1748   524 ?        R    17:30   0:00 /bin/sh /usr/bin/xulrunner-1.9.1 --gre-version
dl       10978  0.0  0.0   3040   868 pts/2    R+   17:30   0:00 grep --color=auto couchdb
```

---

