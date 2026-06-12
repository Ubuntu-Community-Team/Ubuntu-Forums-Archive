---
title: "[SOLVED] Intrepid and build-essential package"
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jett on 2008-09-22
I installed Intrepid on my desktop last night. Wanted to see if it supports the P45 and ICH10R chipset (Hardy does not). I was successfully able to install it and video, sound, and networking were all working. Since I have a widescreen monitor, I wanted to install the ATI binary drivers.

One of the packages it needs is build-essential. When trying to apt-get the meta package, I get an error about a dependency for g++. I understand that not all packages are perfect (yet). Has anybody installed build-essential on intrepid? Seems like a common package to be missed out.

---

### Post by Holonet on 2008-09-22
I just installed it with no problem.  I'm on Intrepid 64 bit though, so it could be a different package if you're running 32-bit.  Someone with 32-bit could chime in here and check as well.

---

### Post by jett on 2008-09-22
thinking it might be due to bad entries in apt's sources.list, I changed the source server in Software Sources to another serve. Did apt-get update and attempted to install build-essential ...

It worked!!!

Everything ok now.

---

