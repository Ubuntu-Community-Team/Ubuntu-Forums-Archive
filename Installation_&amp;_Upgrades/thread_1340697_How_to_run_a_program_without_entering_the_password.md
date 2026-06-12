---
title: "How to run a program without entering the password"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by beemzet on 2009-11-28
hi all,


I've installed thinkorswim in /usr/local/ folder using 'sudo ./thinkorswim.sh' command. However using the menu I wasn't able to open the application so I had to add gksudo in front of /bin/sh "/usr/local/thinkorswim/thinkorswim" in the menu. Now the program starts fine, but it asks me to enter the password every time I start it. How can I start the program without entering the password? And why do other programs like livestation (installed in the same folder) start without asking the password?

Thanks for your answers.

---

### Post by audiomick on 2009-11-28
The one you can start belongs to you, the one you can't belongs to root.
you need to change the permissions on the file so that you have the right to run it.

---

### Post by beemzet on 2009-11-28
> **audiomick said:**
> The one you can start belongs to you, the one you can't belongs to root.
you need to change the permissions on the file so that you have the right to run it.

thanks, it works now

---

