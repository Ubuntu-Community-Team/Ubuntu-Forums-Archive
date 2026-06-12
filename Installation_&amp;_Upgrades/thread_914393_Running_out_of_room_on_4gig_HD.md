---
title: "Running out of room on 4gig HD"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by Bridge51 on 2008-09-08
Can i mount other (16) as 'home or something?

I've been installing programs on my EEE 901 (i have the 4gig/16gig version, linux) and I have run out of room on the 4 gig. I want to know what i can do to put programs onto the other hard drive?  

or is this just for files/documents, not programs?

---

### Post by Predator106 on 2008-09-08
Mount other 16? Do you have another Hard drive that has 16 gigs free? Or is it a different partition?

---

### Post by Bridge51 on 2008-09-08
the eee pc 901 has two internal hard drives, a 4 gig and a 16 gig. the os is run off of the 4 gig

---

### Post by Partyboi2 on 2008-09-08
You could look at moving your /home folder to its own partition.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Predator106 on 2008-09-11
Well I think he wants to have installed programs (via the package manager) be on that hard drive, in which case the /home move wouldn't help.

---

### Post by mattduckman on 2008-09-11
typing
```
sudo du -sh /*
```
will reveal which directory is taking up the most space ... that's the one that should be moved to it's own drive (it'll will probably be either /home, /usr, or /var)

then follow the instructions in the link a couple posts up

---

