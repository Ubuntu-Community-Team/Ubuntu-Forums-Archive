---
title: "Trouble installing software"
date: 2005-05-07
forum: Installation &amp; Upgrades
---

### Post by makimonaco1 on 2005-05-07
I am totally new with LINUX. My Company installs WINDOWS based RADIUS servers and I am trying to re-orient them towards LINUX.

I have installed Ubuntu Warty Warthog 4.10 on my Celeron 2.4 system and everything seemed to go okl: I can go on the net, edit files...

I downloaded a RADIUS package called freeradius from [www.freeradius.org](www.freeradius.org) into my /home/maxo directory. Following the install instructions from that directory I enter the command line:

[COLOR=Navy]maxo@ubuntu:~/freeradius-1.0.2 $[/COLOR] [COLOR=Red]./configure[/COLOR]

and get the following result:

[COLOR=Red]loading cache ./config.cache
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH[/COLOR]
Can you help me?

Thanks.

---

### Post by XDevHald on 2005-05-07
[QUOTE=makimonaco1]I am totally new with LINUX. My Company installs WINDOWS based RADIUS servers and I am trying to re-orient them towards LINUX.

I have installed Ubuntu Warty Warthog 4.10 on my Celeron 2.4 system and everything seemed to go okl: I can go on the net, edit files...

I downloaded a RADIUS package called freeradius from [www.freeradius.org](www.freeradius.org) into my /home/maxo directory. Following the install instructions from that directory I enter the command line:

[COLOR=Navy]maxo@ubuntu:~/freeradius-1.0.2 $[/COLOR] [COLOR=Red]./configure[/COLOR]

and get the following result:

[COLOR=Red]loading cache ./config.cache
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH[/COLOR]
Can you help me?

Thanks.[/QUOTE]
 You'll need to install the compiler for warty, goto **System > Administration > Synaptic Package Manager **then type in the **Search **tool "**gcc**" once you have done that, do the ./configure command again and you should be set :D

---

### Post by makimonaco1 on 2005-05-07
Thanks, that did it.

---

