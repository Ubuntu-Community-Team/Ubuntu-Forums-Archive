---
title: "404 Not Found On Repository France Archive tzdata"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by ifthengoto on 2007-04-24
I received the update notification this morning but when I try to perform the update I get this error message:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007e-0ubuntu0.7.04_all.deb](http://fr.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007e-0ubuntu0.7.04_all.deb)
404 Not Found

---

### Post by bapoumba on 2007-04-24
Hello,
may be the repos have not been synced yet. See if it works later on, or change the repos in your sources.list to use the main ones (delete fr.) if you cannot wait.

---

### Post by Jeumeu on 2007-04-24
I got the same trouble.

It seems that this repos is missing from the french site.

Edit your /etc/apt/sources.list file and change every "fr.ubuntu" into "ubuntu".

It worked for me.

---

### Post by ifthengoto on 2007-04-24
Thanks - changed the repos list and it now works.

---

