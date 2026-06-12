---
title: "No &quot;New Distribution Avaliable&quot; message in 7.10"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by linuxNewb on 2008-08-28
I have been using Ubuntu 7.10 for far to long because I cannot use the update manager for a dist-upgrade. There is no "New Distribution Available" message. I'm sure that this is an easy fix, but I cannot find it anywhere.

I'm now upgrading the "old-school" way with:

```
sudo gedit /etc/apt/sources.list
change every word gutsy to hardy (be sure to leave the # in front of cd)
sudo apt-get update
sudo apt-get dist-upgrade
```

So far, so good. I'll report any problems that I encounter, if any.

Does anyone know what might have caused the "New Distribution Available" message to not show up in the update-manager?

---

### Post by aysiu on 2008-08-29
I believe you need to run the command ```
gksu "update-manager -d"
``` to get that to appear.

---

### Post by cariboo on 2008-08-29
I used the search and replace function in gedit when I upgraded from hardy to intrepid, it worked quite well.

Note: this was just after the repositories had opened and the update-manger -d option didn't work.

Jim

---

