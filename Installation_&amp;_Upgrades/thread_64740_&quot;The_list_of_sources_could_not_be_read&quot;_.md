---
title: "&quot;The list of sources could not be read&quot; problem with sudo"
date: 2005-09-12
forum: Installation &amp; Upgrades
---

### Post by Croquer on 2005-09-12
Hi im trying to install Apache Server in my ubuntu. Im writing in the terminal root the folowing line:

sudo apt-get install apache2

the answer is:

E: Type '$sudo' is not known on line 27 in source list /etc/apt/sources.list
E: The list of sources could not be read.

please help  me....
Thanks

---

### Post by herissonjovial on 2006-12-11
Hello, i have the same problem : "Dist parse error"

it appears just after i made two modifications:
[INDENT]First: editing the /etc/apt.sources.list manually,[/INDENT]
[INDENT]Second: disable the locale CD "déposit place"  from the synaptic GUI[/INDENT]
(sorry for my poor english)

Errors are located in two files:

[INDENT]*  /etc/apt.sources.list[/INDENT]
[INDENT]*  /etc/apt.sources.list.d/edgy-universe.list[/INDENT]

The symptom is that Synaptic can't run anymore :s!
(neither in shell)
thanks for help,

HJ

---

