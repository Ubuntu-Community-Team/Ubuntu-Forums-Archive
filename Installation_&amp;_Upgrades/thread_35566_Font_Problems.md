---
title: "Font Problems"
date: 2005-05-19
forum: Installation &amp; Upgrades
---

### Post by JaF on 2005-05-19
Hi everyone,

I don't seem to have any Truetype fonts installed in my /usr/lib/X11/fonts/ directory. How do I go about installing them and where can I get them from?

---

### Post by dekoi on 2005-05-19
The hard way?

Terminal: sudo apt-get msttcorefonts

The easy way?

Synaptic

Not sure if they're in the restricted repos. or not. You may have to
uncomment the restriced repositories list, which has already been 
covered in forums.

---

### Post by d-n-r on 2005-05-19
[QUOTE=dekoi]The hard way?

Terminal: sudo apt-get msttcorefonts

[/QUOTE]

add 'install' after apt-get to make it work :)

greetings

---

### Post by dekoi on 2005-05-19
Good catch d-n-r, sorry, I forgot the important part there: "install"

---

