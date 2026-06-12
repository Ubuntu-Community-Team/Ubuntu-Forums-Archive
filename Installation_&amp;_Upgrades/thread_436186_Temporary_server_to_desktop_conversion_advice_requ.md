---
title: "Temporary server to desktop conversion advice requested"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by bryan986 on 2007-05-07
Hello,

My main computer is going in for repairs. I am going to install the desktop components onto a computer that is running the server edition so I have something to use in the meantime.

I know doing the install is easy enough with the ubuntu-desktop package, but after that...

I would like to either remove the entire ubuntu-desktop set of packages, or disable the gnome desktop manager (gdm) from starting up automatically.

Could anyone help with either of these options or add any other helpful information?

---

### Post by ohgod on 2007-05-07
I'm not sure how exactly to uninstall all the ubuntu-desktop packages, but preventing gdm from starting isn't too hard:

-chmod the /etc/init.d/gdm script to be non-executable (sudo chmod 644 /etc/init.d/gdm)
-or, I believe you could do it via the System->Administration->Services section (uncheck the box next to the gdm service)

---

