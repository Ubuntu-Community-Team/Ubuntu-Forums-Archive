---
title: "trying to install programs, no success"
date: 2017-10-03
forum: Installation &amp; Upgrades
---

### Post by gufghur on 2017-10-03
Hi all,

To get a VPS running, I'm trying to install some additional software such as [SIZE=2]TeamViewer or [/SIZE]AnyDesk.

After downloading these, software manager opens and I click the install button, but nothing happens... any idea's?

Greetings, and thanks in advance
Guf.

---

### Post by Autodave on 2017-10-03
Download *gdebi *and then use that program to install Teamviewer.  If *Anydesk* is a .deb file, gdebi will also work on that (or any .deb file).

The thing is this: you need other programs (dependencies) to run most files that you download. Gdebi will get those for you and install them with the program.

---

### Post by TheFu on 2017-10-03
If you want remote access, use ssh.

---

