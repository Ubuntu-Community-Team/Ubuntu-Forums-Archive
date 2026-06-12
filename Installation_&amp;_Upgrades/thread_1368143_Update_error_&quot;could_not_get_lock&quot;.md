---
title: "Update error &quot;could not get lock&quot;"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by GkProf on 2009-12-30
When I try to install updates with Update Manager I get this error:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

This in 9.04.

Any remedies or suggestions much appreciated. Relative beginner (I just dabble in Ubuntu), so please don't assume too much.

---

### Post by MelDJ on 2009-12-30
are you running synaptic/add remove while you are running apt-get? that might be the cause
or maybe you could change your software server

---

### Post by GkProf on 2009-12-30
Not sure. I go to System > Admin > Update Manager, then click Install Updates. That's when the error pops up.

---

### Post by MelDJ on 2009-12-30
does this happen all the time? if you reboot your computer and run update manager, does this happen?

---

### Post by GkProf on 2009-12-30
It happened last time I booted Ubuntu, but didn't have time to mess with it then. Today when I booted and ran updates i got the same error as before I rebooted.

---

### Post by MelDJ on 2009-12-30
maybe you can try 
sudo pkill apt

---

### Post by GkProf on 2009-12-30
OK, looks like that might have worked. Ran the command in Terminal and then Update Manager, and it's proceeding to install updates as I type this. 

Have time to expalin what's going on with this situation? Am I going to need to redo this each time?

---

### Post by MelDJ on 2009-12-30
i think another instance of apt-get didn't close properly. since, only one apt-get can run at a time (synaptic, add/remove, update manager are all types of apt-get) update manager wont run. hence we use pkill to terminate apt-get.

---

### Post by GkProf on 2009-12-30
Thanks for the explanation. The last 2 replies aren't showing up in my browser here, but I got the via email. Thanks for your help.

---

