---
title: "Ubuntu 10.10 Synaptic &quot;Mark Packages by Task&quot; MISSING"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by simonz on 2010-10-12
The Synaptic Package Manager in Ubuntu 10.10 no longer has the option "Mark Packages by Task".  In previous versions it was under the "Edit" menu.

Is there a way to get it back or is it hidden in other menus?

---

### Post by tibasic on 2010-10-13
I've noticed this problem as well. Exit Synaptic, open a terminal and type "sudo apt-get install tasksel" once it is finished the option will be in Synaptic again.

What's even more disturbing is that myphpadmin doesn't seem to be in the repo anymore...

---

### Post by bogdan.s on 2010-10-13
> **tibasic said:**
> I've noticed this problem as well. Exit Synaptic, open a terminal and type "sudo apt-get install tasksel" once it is finished the option will be in Synaptic again.

What's even more disturbing is that myphpadmin doesn't seem to be in the repo anymore...

Just type in "phpmyadmin" in synaptic's search box. Thanks for "sudo apt-get install tasksel"; I don't know how you guys get to know all this stuff.

---

### Post by simonz on 2010-10-13
Totally amazing! "sudo apt-get install tasksel" worked perfectly.

Thanks!

---

### Post by DrAcid on 2010-10-13
Yes, it does work perfectly! Thank You!

Btw, do You know WHY exactly they've removed the function? it's like just ~300kb... and the 100.10 CD had ~7mb extra space... ?

---

