---
title: "broke my sources.list"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by Bluestars on 2010-08-08
I was trying to install Tor and deleted a couple lines out of the sources.list.  I think I may have deleted something I wasn't supposed to. When I try to run the Update Manager I get  "An unresolvable problem occurred while initializing the package information.  Please report this bug against the 'update-manager' package and include the following error message:  'E:Malformed line 56 in source list /etc/apt/sources.list (dist), E:The list of sources could not be read.'"  How can I fix this?

---

### Post by Nick_Jinn on 2010-08-08
Did you enable the archive repositories? You dont need those. Try uninstalling them.

Hopefully thats it.

---

### Post by xoomer.ap on 2010-08-08
What in line #56 of this file?

---

### Post by Bluestars on 2010-08-08
No, I don't have the archives enabled.    How do I tell which line is 56? When i gedit /etc/apt/sources.list none of the lines are numbered. Is there a way to set it to show numbering? Sorry I'm a noob.  If you would like I could post everything it lists.

---

### Post by xoomer.ap on 2010-08-08
Sorry, I'm not familiar with GEdit, try to activate numbering in options...
Anyway, count up lines in mind, if you want... ;)

---

### Post by oldos2er on 2010-08-08
In gedit, Ctrl-I then type in 56.

---

### Post by Bluestars on 2010-08-08
I rebooted and now my internet doesn't connect on Ubuntu.  I had to get on Windows partition to post this.  line 56 is deb [http://deb.torproject.org/torproject.org/dists/lucid/main/](http://deb.torproject.org/torproject.org/dists/lucid/main/)

---

### Post by xoomer.ap on 2010-08-08
Try to insert commenting symbol "#" in the begin of line:
```
# deb [http://deb.torproject.org/torproject...ts/lucid/main/]("http://deb.torproject.org/torproject.org/dists/lucid/main/")
```
then try:
```
sudo apt-get update
```

---

### Post by oldos2er on 2010-08-08
That line should be deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main

---

### Post by Bluestars on 2010-08-09
Thanks!  It seems adding the # fixed the problem. How would I now go about getting Tor?

---

### Post by oldos2er on 2010-08-09
```
sudo apt-get update && sudo apt-get install tor
```

[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

---

