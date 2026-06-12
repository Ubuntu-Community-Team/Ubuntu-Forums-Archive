---
title: "problems in update manager"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by jameshigley on 2010-06-18
i've been adding and removing packages, and was using gnokii.  I went in to synaptics package manager and completely removed gnokii and ALL of the supporting files.  

Now i cannot install ANYTHING NEW, CANNOT UPDATE, I CAN REMOVE THINGS BUT NOT INSTALL.  I went in to terminal and ran the update manually, and this is what i get:

The following packages will be upgraded:
  libgnomekbd-common libgnomekbd4 libpoppler-glib4 libpoppler-qt4-3 libpoppler5 poppler-utils
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1,110kB of archives.
After this operation, 8,192B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown group 'gnokii' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
j

How do I get rid of this "syntax error:unknown group 'gnokii' in statoverride file
so maybe i can get dpkg towork again?

---

