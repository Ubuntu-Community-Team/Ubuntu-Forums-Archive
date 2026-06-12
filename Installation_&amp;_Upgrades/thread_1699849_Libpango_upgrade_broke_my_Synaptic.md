---
title: "Libpango upgrade broke my Synaptic"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by ThorX89 on 2011-03-04
I ran a system upgrade today and it froze at "unpacking replacement libpango1-common". It just wouldn't go on. The upgrade kept on showing "unpacking replacement ..", the process used zero CPU time, so I killed it, removed the lock and after Synaptic asked me to, I ran sudo dpkg --configure -a.
Now I can't install anything. Everytime I try to, I get an error telling me I should run "sudo apt-get -f install", however, whenever I do that, another endless installation of libpango1.0-common starts.
I tried various things like installing that package manually, removing it and so on, but nothing helped.
Any advice on how to get my package installation system working again is warmly welcome.

---

### Post by ThorX89 on 2011-03-04
Ok. So a reboot did it.
I don't know how to delete my post so I just marked it as Solved.

---

### Post by louisgag on 2011-03-12
I had a similar error with libpango not being able to upgrade to the 11.04 version and I solved it by **manually deleting the /var/...docs/libpango1.0-0 directory** which the dpkg uninstall script of the previous libpango version was complaining not being able to remove...!

---

