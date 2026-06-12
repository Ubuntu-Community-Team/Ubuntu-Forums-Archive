---
title: "having 'ca.archive.ubuntu.com' issues?"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by yazuki101 on 2008-02-01
While trying to install something (drivers and the like) while in the CLI, are you getting the same message I was?

"cannot resolve 'ca.archive.ubuntu.com'"

After hours (maybe days even) of searching on any resource I could I found this archive that gives an explanation. 

[https://lists.ubuntu.com/archives/ubuntu-users/2006-May/079251.html]("https://lists.ubuntu.com/archives/ubuntu-users/2006-May/079251.html")

I figured I would make a new post and get one more resource out there to search for.

---

### Post by taurus on 2008-02-01
Maybe that mirror is down.  Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and pick another site or you can even use the main server.  Then, Refresh it and see if it works now.

---

### Post by yazuki101 on 2008-02-02
whether its down, or its just overloaded either way once i edited the 'sources.list' file by deleting all instances of 'ca.' in any line with 'http://ca.archives.ubuntu.com'. ( I also had to delete '#' in the lines for the backports, they were hashed out for some reason) I was able to download all the files I needed to enable runlevel 4 and get the GUI up.

---

