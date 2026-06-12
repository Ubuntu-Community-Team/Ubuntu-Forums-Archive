---
title: "CompilingEasyHowto"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by shipinomore on 2010-06-24
trying to follow the Compiling easy how to document.
no problem step 1 moved the downloaded file into the /usr/local/src
then right clicked on the file which was /home/larry/Downloads/thunderbird-3.1rc2.source.tar.bz2
and did the extract but was surprised that the source after extract was a file comm-1.9.2 ??
I was looking for one that had much the same name.
I then ran tar xjvf and the filename and at the end I went to step four thinking all was there tried to run make as it stated and error
I wanted to run this version of thunderbird as they have issues in the past with Comcast and setting up and authorizing with the mail server.
are these instructions wrong? what perhaps should be the command listed in step 4
Larry

---

### Post by dino99 on 2010-06-24
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by shipinomore on 2010-06-24
Thank you dino it somewhat the same as the one I was using. Will see if I can get it to work.
Larry

---

### Post by TRoe on 2010-06-24
Did you descend into the extracted source directory (i.e. cd comm-1.9.2) before running ./configure and make?

"comm" probably stands for "cummunicator", which was the name of the old Netscape internet and mail suite from which Firefox and Thunderbird were spawned from.

---

