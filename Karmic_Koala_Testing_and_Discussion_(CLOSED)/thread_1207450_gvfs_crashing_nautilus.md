---
title: "gvfs crashing nautilus"
date: 2009-07-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mrsurb on 2009-07-08
Since latest (Jul 8th) updates I nautilus crashes whenever I try to establish a gvfs, such as browsing a bluetooth mobile or mounting a samba share. The problem persists even if I revert to a previous kernel (2.6.31-2 instead of 2.6.31-1).

Perhaps related, I have also installed the ubuntuone-gnome-client in the previous 24 hours, although that does appear to be working.

Any ideas?

---

### Post by chrisccoulson on 2009-07-08
The ubuntuone client has introduced a crasher in to Nautilus, which is most likely what you are experiencing. See [https://bugs.edge.launchpad.net/ubuntuone-client/+bug/395710]("https://bugs.edge.launchpad.net/ubuntuone-client/+bug/395710")

---

### Post by tad1073 on 2009-07-08
I was experiencing the same issue, uninstalling ubuntone-client and all the dependencies fixed the problem.

I unistalled ubuntu 9.10 and re-installed, then installed ubuntone again that is when I found out that ubuntuone was the culprit.

---

### Post by mrsurb on 2009-07-08
Great - thanks for the prompt help. Beta testing... always an adventure!

---

