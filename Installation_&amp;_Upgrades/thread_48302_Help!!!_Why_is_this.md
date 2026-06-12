---
title: "Help!!! Why is this?"
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by RJARRRPCGP on 2005-07-11
When I go to System>Administration>Synaptic Package Manager and some others from the top menu, why do they fail to respond and then disappear? :mad:

---

### Post by jaranguren on 2005-07-12
I had this problem before when I accidentally changed the owner of /usr/bin from root to some_user using ```
chown -R some_user /usr/bin
```.  Don't ask me why I did it, it just happened.  Anyways, after changing the owner, I couldn't open date/time applet, printer, synaptic, etc. unless I changed it back to root.

I think one thing you can try is to launch synaptic from the terminal or you can also check who owns gksudo first.

Hope this helps.

---

### Post by RJARRRPCGP on 2005-07-12
That was even when I didn't change anything!!! Is this a bug?

---

### Post by az on 2005-07-12
It would be neccessary to see the output of

gksudo synaptic

from a terminal...

---

### Post by RJARRRPCGP on 2005-07-12
[QUOTE=azz]It would be neccessary to see the output of

gksudo synaptic

from a terminal...[/QUOTE]

**sudo** actually just gave me this error message after typing in the above command:

**sudo: unable to** 

Strange. Why is that?

---

### Post by jaranguren on 2005-07-13
can you please post the output of 
```
ls -al /usr/bin/gksu 
```
I just want to see who owns this command.

---

### Post by RJARRRPCGP on 2005-07-13
[QUOTE=jaranguren]can you please post the output of 
```
ls -al /usr/bin/gksu 
```
I just want to see who owns this command.[/QUOTE]

The output of the command is the following:

-rwxr-xr-x  1 root root 18804 2005-04-04 17:08 /usr/bin/gksu

---

### Post by az on 2005-07-13
What does your

/etc/sudoers

file look like? (post it)

---

