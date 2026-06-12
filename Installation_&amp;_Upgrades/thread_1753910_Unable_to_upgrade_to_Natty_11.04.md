---
title: "Unable to upgrade to Natty 11.04"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by cyberjar09 on 2011-05-09
I tried to upgrade to 11.04 from 10.10 but I get this error every time 

```
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/python2.7/libpython2.7_2.7.1-5ubuntu2_i386.deb Bad header line [IP: 91.189.92.162 80]
```

Any ideas on how I can go about resolving this issue?

---

### Post by sanderd17 on 2011-05-09
did you add that resource yourself?

Try going in the software center to edit->software sources and disable something that looks like that line.

Then execute
```

sudo apt-get update

```

If you still have errors, post the output here.

---

### Post by Rubi1200 on 2011-05-09
Hi,
go to System > Administration > Synaptic Package Manager >  Settings > Repositories > Download from and either change it from what you have to Main Server or select Other > Choose best server. Reload from the menu and then try again.

Let me know if this helps.

edit: sanderd17's way is quicker to access Software Sources, but you can still change the Download from part doing it like that too.

---

### Post by cyberjar09 on 2011-05-09
Thanks a lot, modifying the download server fixed the problem. Now on 11.04 :guitar:

---

### Post by Rubi1200 on 2011-05-10
Excellent! Glad you got the problem solved.

Enjoy :-)

---

