---
title: "Scalix - 32 bit .deb on amd64"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by kamil.choudhury on 2008-01-19
So a couple of days ago, I decided that's time to install some kind of groupware on my 7.04 amd64 server to alleviate some of the appointment-related chaos that seems to be taking over my life. Scalix seemed like a good solution, so I decided to run with it. The problem is that they only provide a 32 bit .deb, and the source isn't available to compile it from scratch (boo, hiss). Anyhow, I decided to do a dpkg --force-architecture -i and try and get it to work... 

Which seems to go just fine, until I get this message: 

```
 /opt/scalix/bin/ldapmapper: error while loading shared libraries: libldap_r.so.2: cannot open shared object file: No such file or directory
```

Oops! After doing a bit of digging, I found out that even after installing the ia32-lib compatibility package, the libldap_r.so.2 shared object (seemingly related to ldap?) wasn't in the /usr/lib32 directory. 

Does anyone know where I can get this library? 

Thanks in advance for any suggestions. 

As a sidenote, I'm sure I'm not the only one looking to get Scalix installed on Ubuntu. I'd really like to take any suggestions I get on this thread and work them into an FAQ/step-by-step for the community at large after I get Scalix installed... so get with the suggestions, people! :)

---

### Post by c0met on 2008-01-19
I seem to have a copy of that somewhere on my computer because there is a link to it in /usr/lib (I haven't looked to find out where the file is, though). I remember reading on the forums a while ago that the 32 bit libraries are installed when WINE is installed. It might be worth trying that. Just a suggestion.

---

