---
title: "Synaptic Error"
date: 2006-05-17
forum: Installation &amp; Upgrades
---

### Post by Chapulin Colorado on 2006-05-17
Hi all!  I just installed the latest flight of Dapper.  I also installed the XFCE desktop.  I got through the installation with minimum problems.  At the end of the installation i got an error message from apt.  I decided to ignore it, and reboot into my new Xubuntu system.  All seemed well.  But when i go to install new programs using Synaptic the programs install fine, but at the end I get the same message that i got when i first installed Xubunt.
```
E: xubuntu-docs: subprocess post-installation script returned error exit status 2
E: xubuntu-desktop: dependency problems - leaving unconfigured
```

Even though it does not prevent me from installing the programs I would like to get rid of it.  Any ideas are welcomed, and thanks in advanced for your help.  If you need me to post any specs on my system let me know, or anything for that matter. 

Thanks!

---

### Post by louis_nichols on 2006-05-17
Did you try using synaptic's fix packages feature? It might do the trick.

---

### Post by Chapulin Colorado on 2006-05-17
Hi! Thanks louis_nichols for your reply.  I gave it a go but it seem's that I am still getting the same error.  Any other suggestions?

Thanks again

---

### Post by louis_nichols on 2006-05-17
try this command in terminal:

sudo dpkg --configure -a

---

