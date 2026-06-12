---
title: "Will Ubuntu 8.10 come with Mono 2.0 ?"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by j23tom on 2008-10-08
Will Ubuntu 8.10 come with Mono 2.0 ?

---

### Post by puntarenas on 2008-10-08
According to the package developer, it will not:

-> [Will Mono 2.0 (rc) be included in 8.10?](https://answers.launchpad.net/ubuntu/+source/mono/+question/44628)

---

### Post by EnGorDiaz on 2008-10-08
there are many topics regarding to mono being in ubuntu fullstop and mostly the developers dont want to put it in because its unready aparently

im not sure i just know i have to download the gui version maybe it does come in default

---

### Post by directhex on 2008-10-08
Intrepid will ship with 1.9.1. I'm sure unofficial backports will be created once there are 2.0 packages to backport (Mono cannot get an 'official' backport as the risk of regression is too great)

---

### Post by fd0man on 2008-10-13
I've created a script that will install a parallel Mono (Mono 2.0) in ${HOME}/opt.  It also installs MonoDevelop 2.0 Alpha 1 current from SVN.  See [the post on my blog]("http://www.trausch.us/2008/10/13/want-to-play-with-mono-20-so-do-i/") which talks about it and provides many, many more details.

Just to make sure it's well-known and understood, I'll repeat part of what I said there, here:  A few words about the script: ***This script is released under the terms of the GNU General Public License, Version 3. It is version 3 ONLY. There is NO SUPPORT for this software; I wrote it for myself, and it may change or it may stagnate. I provide it in the hope that it is useful to someone out there other than myself, but it is AS-IS, WITHOUT WARRANTY, UNSUPPORTED software. If it changes your dog’s gender, bursts your house into flames, destroys your whatchamacallermicroflobbermajag, do not come and yell at me.*** That having been said, I welcome any modifications (at least to view them). You can modify it for your own use, you can share it (in fact I expect you to!) and you can tinker with and tweak it. Suggestions? Welcome! Comments? Welcome! Flames? Hey, free speech is your right…

---

