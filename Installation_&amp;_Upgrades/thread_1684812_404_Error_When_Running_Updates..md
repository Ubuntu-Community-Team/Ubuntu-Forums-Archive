---
title: "404 Error When Running Updates."
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by John Lyster on 2011-02-09
system/about shows I have V11.04.
When I start Ubuntu the update man shows rec'd updates, but won't get past 'to install or remove software you need to uthenticate.' after I've given my admin password. 
The 'details' of this window leads me to <https://launchpad.net/aptdaemon/> but no description of what I should do there.

If I, then close that frozen authenticate window update man starts to continue but then hangs and tells me it cannot connect and download the needed package files. 
The 'details':
Failed to fetch [http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-beta/google-chrome-beta_9.0.597.84-r72991_i386.deb](http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-beta/google-chrome-beta_9.0.597.84-r72991_i386.deb) 404  Not Found [IP: 74.125.127.190 80]

I've had zero problems upgrading in the past.
Some help?

So far I've used Ubuntu infrequently as I have three major win/only programs that I use almost daily.

Pentium P4, 2G ram

---

### Post by uRock on 2011-02-09
When you open System> Administration> System Monitor what version does it show?

PS. I am changing the thread title to a more related title.

---

### Post by John Lyster on 2011-02-09
OK. I went back to square one.
From the choices at the grub screen, I chose the repair option.
All's well now.
V10.10 is back on the 'about' screen.
No updates needed.
I have no idea how V11.04 was semi installed.

---

### Post by uRock on 2011-02-09
I am glad that they finally fixed the about bug. I am glad your problem is cleared up.

---

