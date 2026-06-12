---
title: "Ungodly-frustrated with 7.10 upgrade"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Baphijmm on 2007-10-20
I tried this before, and nothing has helped at all.

1. The Distribution Upgrade manager hangs while "Checking Package Manager", in either the first or second step (entirely depends upon whether or not it hung on the first step if it will on the second).

2. Let aforementioned manager run for >12 hours; absolutely no sign of any sort of advancement had been made.

3. Downloaded the Alternate CD; the manager from it would get hung up in the same place.  Now, the disk won't operate as it is supposed to, neither being recognized as an upgrade disk nor responding to the command given (gksu "sh /cdrom/cdromupgrade").

4. The process named "gksu" acts like a virus itself, regenerating itself every time it is killed in an attempt to restart the upgrade.

5. Changing sources does nothing, as while the upgrade is running, it changes them back to the main server, which is where the manager hangs on the second step.  In addition, in order to actually change sources, for some god-awful reason I have to physically go into sources.list and manually change every single one.

NOW, with this all in mind, and the fact that I refuse on principle to run a clean install (because, if the upgrade were developed properly, that should not be necessary):  What should I do to rectify this horrendous upgrade?  I like Ubuntu, but if this upgrade isn't fixed by Sunday evening, I'm going to change Linux distros, because this is ridiculous.

---

### Post by Arenlor on 2007-10-20
This is unique, can you try
```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```and see if it does the same?

---

### Post by Baphijmm on 2007-10-20
```
Could not download the upgrades
The upgrade aborts now. Please check your internet connection or installation media and try again. 
Failed to fetch http://mirrors.cs.wmich.edu/ubuntu/pool/main/t/tzdata/tzdata_2007h-0ubuntu0.7.10_all.deb 404 Not Found
```
That was the end result.  In other words, it didn't work.

---

### Post by Arenlor on 2007-10-20
404 not found is true, quit using a mirror and switch to using just the main Ubuntu archive. That file just does not exist on that mirror.

---

### Post by Baphijmm on 2007-10-20
Okay, how does one go about doing this?  This is the only upgrade I've ever had to change sources on to even attempt to complete it (since 5.10), so I have no idea what I'm doing.

---

### Post by Arenlor on 2007-10-20
Go to System > Administration > Software Sources and under download from choose main server or your country's server.

---

### Post by Baphijmm on 2007-10-20
As I had said before, that actually doesn't work on this box for some reason; however, I went in and manually changed the sources over to what I can only assume was the main server.  I had it written down for some reason, so I just typed it in, and it seems to be progressing now.  I suppose I'll update later on the progress.

---

### Post by Arenlor on 2007-10-20
Weird, but for whatever reason your mirror wasn't existing there.

---

### Post by Baphijmm on 2007-10-20
Yes, that seems to have fixed it; I'm on 7.10 right now.

---

