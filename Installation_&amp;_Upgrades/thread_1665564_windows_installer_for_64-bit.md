---
title: "windows installer for 64-bit"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by krisnam on 2011-01-12
I have a Ubuntu 10.10 live cd for 32-bit.  However it does not work with my system--I am guessing it has something to do with having more than 4 gigs of ram.

Anyway I am wondering if there is a way to install ubuntu 10.10 64-bit with Windows 7 64-bit.

---

### Post by mikewhatever on 2011-01-13
While the 32bit version might not be able to access all the RAM, it's highly unlikely that it didn't work because of that. If you want to try the 64bit cd, go ahead and don't let anyone stop you, but you can also specify what the problem was with.

---

### Post by Mark Phelps on 2011-01-13
> **krisnam said:**
> ... Anyway I am wondering if there is a way to install ubuntu 10.10 64-bit with Windows 7 64-bit.

IF you install "with" Windows 64-bit, you will be installing INSIDE Windows.  Is that what you want?

IF not, you need to boot from a CD and install that way.

BTW, there were some problems a while back installing MS Windows in PCs that had more than 4GB of memory -- which was solved (then) by removing the extra memory for the installation only.

But, I would think that those problems would NOT affect installing Ubuntu.

---

### Post by ottosykora on 2011-01-13
as it is apparently not clear what exactly you are after, you have to tell us more.
You can install any 32bit operating system on a PC with 64bit architecture, 32bit OS will simply not use the full ram, that is all.

But as you say 'with windows 64bit' this can mean you want install wubi. The installer runs under windows, the installation is then later running not under windows as many people think, but runs natively as linux, it is just using virtual disk volumes for that. But here is the problem: the files for the booting such system are not running right then, so you will be best to make sepparate partition and install ubuntu there, 32 or 64.

---

### Post by ottosykora on 2011-01-13
as it is apparently not clear what exactly you are after, you have to tell us more.
You can install any 32bit operating system on a PC with 64bit architecture, 32bit OS will simply not use the full ram, that is all.

But as you say 'with windows 64bit' this can mean you want install wubi. The installer runs under windows, the installation is then later running not under windows as many people think, but runs natively as linux, it is just using virtual disk volumes for that. But here is the problem: the files for the booting such system are not running right then, so you will be best to make separate partition and install ubuntu there, 32 or 64.

---

