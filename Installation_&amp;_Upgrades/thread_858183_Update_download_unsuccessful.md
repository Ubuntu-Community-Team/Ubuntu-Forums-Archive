---
title: "Update download unsuccessful"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by Bobrm2 on 2008-07-13
Running Hardy Heron 8.0.4. 

  Received while attempting to run upgrade notice. Is this the correct forun/is there sufficant information to isolate the problem, or this a bug?

Thank you

[B]non-free/a/acroread/acroread_8.1.2-0medibuntu6.1_i386.deb
  404 Not Found [IP: 91.121.38.148 80][/B]

---

### Post by Pumalite on 2008-07-13
Post the complete output of:
sudo dpkg --configure -a

---

### Post by Vadi on 2008-07-13
It might be that your local update mirror is down right now. To change it, you can go to system - administration - software sources

---

### Post by Bobrm2 on 2008-07-13
Pumalite,


bob@bob-desktop:~$ sudo dpkg --configure -a
bob@bob-desktop:~$ 

??
Bob

---

### Post by bapoumba on 2008-07-13
Please post the output to :
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Pumalite on 2008-07-13
Check your connection too. Or try a different server.

---

### Post by Bobrm2 on 2008-07-13
Change update servers, from USA to Main. All is well. Thank each of you for your help. Oh, I suspect that there is some way to thank you, other than in this post?

Bob

---

### Post by Vadi on 2008-07-13
The lil medal button bottom-right of each post is a thank button.

---

### Post by ajgreeny on 2008-07-13
There was an update of acroread yesterday and again today.  When I tried to use update manager to get it today it failed for some reason, several times.  I immediately tried synaptic instead and suddenly all was well.  I don't know if they are using different servers for the updates, but it seemed a little odd that one worked, the other didn't.  Any clues why?

---

