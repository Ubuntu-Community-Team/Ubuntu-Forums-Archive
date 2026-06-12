---
title: "linux-source-2.6.20 not authenticated"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by mtb-cliff on 2007-06-08
Hi folks, 

I need to compile a new kernel, however, when I go to install the linux-source-2.6.20 package using Synaptic, it brings up a warning that the source could not be authenticated. I have not had this show up on other packages. Is this something specific with the linux-source-2.6.20 package? Is it safe to use - I need to build a kernel for a vpn, so I need to know that it is clean?

Thanks, Cliff.

---

### Post by ibnbattuta on 2007-06-11
I have the same problem. Trying with the normal update manager in 7.04 to update linux-headers-2.6.20-16 which together with a couple of other packages are listed as "NOT AUTHENTICATED". See screenshot. 

Anybody know why these particular packages come up as not authenticated? 

Am I doing something incorrectly? 

Does this signify I shouldn't install them? 

Ibn Battuta.

---

### Post by merlinus on 2007-06-11
This issue has been discussed on a thread in General Help.

Someone said running:

sudo apt-get (or) aptitude update

will resolve the problem, as it reloads the sources in /etc/apt/sources.list

-merlin

---

### Post by ibnbattuta on 2007-06-11
Great! 

the dialogue disappeared. thx for helping a newbie. 

:-)

Ibn battuta.

---

### Post by mtb-cliff on 2007-06-22
Yes, Thanks. took me a while to get back to this.

---

