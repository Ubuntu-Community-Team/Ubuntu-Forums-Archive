---
title: "synaptic update error"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by pradeepadapa on 2007-03-24
hello guys , i m getting an error when i try to update the synaptic manager....

i get the following error

couldnot download all repository indexes
[http://ubuntu.beryl-project.org/dists/edgy/Release:](http://ubuntu.beryl-project.org/dists/edgy/Release:) Unable to find expected entry  main-edgy/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://in.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:](http://in.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz:) Sub-process gzip returned an error code (1)
[http://in.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:](http://in.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz:) Sub-process gzip returned an error code (1)


can anyone plse tell me how to solve this problem.....

---

### Post by taurus on 2007-03-24
Open a terminal, Applications -> Accessories -> Terminal, and run these two commands.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by pradeepadapa on 2007-03-25
thanx man, though urs is not the answer which i hoped to be correct , i hav rectified the sourcs.list nd just changed the sources site address.....

however thankyou fr ur advice

---

