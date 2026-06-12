---
title: "problem with apt repositories!!!"
date: 2005-03-26
forum: Installation &amp; Upgrades
---

### Post by cypher64 on 2005-03-26
i have installed ubuntu hoary successfully and i have used apt-get many times before but  last time i tried to execute "apt-get update" i got the following error :

Error [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
  Unable to connect to localhost:4001 (127.0.0.1). - connect (111 connection denied)

at the sources.list i use these mirrors:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse

thanx in advance

---

### Post by Ryujin on 2005-03-26
Go ahead and comment those out, the repositories won't be up until after the final relese of hoary

---

### Post by cypher64 on 2005-03-27
i finally found the solution. the mistake was mine , i forget that i have installed anon-proxy.
 despite the fact that anon-proxy didn't run as a process (so i couldn't see it) , during the installation some apt variables had been modified that's why apt-get was trying to connect to localhost:4001!!!
anyway , i remove the pkg and now all works fine!!

---

### Post by lothar_m on 2005-06-05
I had the same problem!

i removed anon proxy and all is fine.
thanks for the help.

---

