---
title: "errors when installing alpine"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by plasmafusion on 2008-09-08
hey all :)
just switched from debain etch to ubuntu 8.04 server on my mail/web/file server and have had no luck installing the pine email client. i saw [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=362724&highlight=install+alpine") thread which recommends the alpine client but when i attempt to install it using apt-get install alpine i get the following error message

> Reading package lists...
Building dependency tree...
Reading state information...
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  pine: Depends: libldap2 (>= 2.1.17-1) but it is not installable
        Depends: libssl0.9.7 but it is not installable


anyone got any ideas?
cheers,
[B]
**EDIT** should have tried this first but i did "apt-get -f install" which removed the broken pine package and alpine installed fine...sorry to have started this thread.[/B]

col

---

### Post by Partyboi2 on 2008-09-08
Do as it says, in a terminal type
```
sudo apt-get -f install 
``` to fix broken dependencies.

---

### Post by plasmafusion on 2008-09-08
thanks Partyboi2...i must have been editing my first post as you were typing your reply.
if a mod would kindly delete this thread i'd appreciate it...even if it's just to make me look a bit less stupid ;)
cheers.

---

