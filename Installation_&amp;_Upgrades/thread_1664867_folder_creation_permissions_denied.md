---
title: "folder creation permissions denied"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by Pedroparamo on 2011-01-11
I'm trying to create a folder using the archive manager to install Resin (web server) in the usr/local folder but I get the error message 'error creating directory: Permission denied.'  

Is this the easiest way to install an app--by using the Archive Manager--and if so how do I establish the correct permissions.

Pedro Paramo

---

### Post by nothingspecial on 2011-01-11
Extract the archive to our desktop

Press Alt-F2

Type
```

gksudo nautilus
```

Then your password.

Then drag it into /usr/local

---

