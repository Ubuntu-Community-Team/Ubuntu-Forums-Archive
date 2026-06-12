---
title: "Problem on ubuntu"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by Vampiree on 2008-08-10
I have a problem on ubuntu.When I want to install package from Add/Remove
it don't work and says :

[I]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I]

---

### Post by Non Plus Ultra on 2008-08-10
and what happens when you run "dpkg --configure -a" in a terminal and try again?

---

### Post by kelean on 2008-08-10
So open up a console window and type 

sudo dpkg --configure -a

It should fix the problem.

---

### Post by Vampiree on 2008-08-10
> **kelean said:**
> So open up a console window and type 

sudo dpkg --configure -a

It should fix the problem.

I typed it bot my problem didn't solve.
:mad::icon_frown:](*,)

---

### Post by Non Plus Ultra on 2008-08-10
Don't you think it's useful for the other forum members if you could give a little more info? 
I've done a search on your error on the forum and a lot of suggestions are done here and there. Try that first.

---

### Post by kelean on 2008-08-10
What was the output when you typed sudo dpkg --configure -a

You could also try

sudo apt-get -f install

That might help

Some more info would help

---

