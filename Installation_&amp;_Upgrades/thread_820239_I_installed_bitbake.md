---
title: "I installed bitbake"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by somepallihanu on 2008-06-06
Hi,
   I installed  bitbake throgh synaptic manager in ubunutu 7.10. 
   
   after typing the [COLOR="Green"]$bitbake [/COLOR]i got the following message... 

   [COLOR="Red"]FATAL: Please set the 'PERSISTENT_DIR' or 'CACHE' variable.[/COLOR]
 
   [COLOR="Green"]Please Help me regarding this... How to resolve this problem[/COLOR]

     Advanced Thanks

---

### Post by MeduZa on 2009-02-06
same problem, but after modify :

TMPDIR = "${HOME}/OE/${DISTRO}-stable/"
to
TMPDIR = "${HOME}/OE/${DISTRO}/stable/"

---

### Post by todd376 on 2009-12-23
so it was suggested that i modify the following to correct my bitbake error


TMPDIR = "${HOME}/OE/${DISTRO}-stable/"
to
TMPDIR = "${HOME}/OE/${DISTRO}/stable/"

i am new to this, can someone give me detailed instructions on how to perform this action?

---

