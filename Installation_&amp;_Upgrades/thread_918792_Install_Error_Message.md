---
title: "Install Error Message"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by soho2014 on 2008-09-13
Does anyone know how i can fix my install process.

I get this error message.

'E:Type '“deb' is not known on line 56 in source list /etc/apt/sources.list, E:The list of sources could not be read.'


No matter if I used the Synaptic package manager, or add/remove programs, I get the same error message.  Looking with the terminal, I don't even see at sources.list, E:

i do see sources.list though.

---

### Post by Partyboi2 on 2008-09-13
Can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /etc/apt/sources.list
```

---

### Post by soho2014 on 2008-09-13
> **Partyboi2 said:**
> Can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
cat /etc/apt/sources.list
```

Thanks very much for your reply, but I was able to fix the problem by editing that source list.  When I tried to install automatix2, that's what screwed it all up.  I just deleted one line of the source.list and do a couple of terminal commands that someone suggested.:guitar:

---

