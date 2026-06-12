---
title: "Upgrade issue; failed to fetch"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Xoanan on 2008-04-24
Hi All

I am one of the beta testers for the 8.04 release and I get upgrade notifications almost daily.  Right now, I am trying to do the latest upgrade and my system is hung at one point.  Here is what it says.

```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-6/openjdk-6-jre-lib_6b08-0ubuntu1_all.deb 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-6/openjdk-6-jre-headless_6b08-0ubuntu1_i386.deb 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-6/openjdk-6-jre_6b08-0ubuntu1_i386.deb 404 Not Found [IP: 91.189.88.31 80]
```

I know that its talking about jre here. Any thoughts?:popcorn:

---

### Post by Patsoe on 2008-04-24
That could just be accidental. Could you update your package list and try the fetch again?

---

### Post by lordrick112 on 2008-04-24
Also you could try to change your software sources and pick a different server.
Ive ran into a few problems like that, not being able to fetch some repositories and changing the server seemed to help. Change the Main server option using the dropdown arrow, then select "other", then select "Select Best Server". It will ping other download servers and choose the best one for your location.

Hope this helps yah out!

---

### Post by Xoanan on 2008-04-24
Cool suggestions, gang!  I do appreciate it!  Thanx!

---

### Post by ptcbus on 2008-04-24
The servers are overcrowded. Try using torrent files. I used torrent to upgrade. See [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

---

