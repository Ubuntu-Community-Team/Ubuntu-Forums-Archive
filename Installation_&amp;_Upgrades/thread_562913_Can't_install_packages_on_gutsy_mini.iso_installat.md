---
title: "Can't install packages on gutsy mini.iso installation"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by penman242 on 2007-09-29
I just installed a cli system using the gutsy mini.iso dated 9/24/07.  The install went fine, but now I have booted into the system and tried:

sudo aptitude install xorg kdm kde-core    (plus some other things)

It sees the repos and tells me what all is going to be installed, including dependencies, indicating I certainly am connected to the internet and that /etc/apt/sources.list is okay.

But when I say Yes to go ahead with the installation, I get a bunch of:

Temporary failure resolving 'us.archive.ubuntu.com'   for each package, and nothing at all gets installed.

Anyone know of a solution?  :confused: Thanks!

---

### Post by pxwpxw on 2007-09-29
I just browsed us.archive.ubuntu.com and it was OK. Try it again.

---

### Post by penman242 on 2007-09-29
Yes, I see I can browse the archive, too.  But I still have the problem.  It sees the repos.  It tells me how much has to be downloaded and exactly what files, including dependencies.  It is only when I give the final Yes to do the installation that I get the error.    Thanks for your reply.

---

### Post by pxwpxw on 2007-09-29
Right, I suppose you ran aptitude update, should have shown a problem then. But I'm just guessing now, I'll leave it for someone else to help.

---

