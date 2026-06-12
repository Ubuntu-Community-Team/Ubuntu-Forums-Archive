---
title: "mutual dependency paradox!!"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by choben on 2008-04-03
I want to compile a package that requires c++ compiler so I try to download the latest version g++ 4 but it depends on libstdc++6-4.1-dev, which wont install because it depends on g++4 ...
WhEn dOeS It eNd?
Someone else had the problem, but not with a response that I could relate:
[http://ubuntuforums.org/showthread.php?t=411180](http://ubuntuforums.org/showthread.php?t=411180)

---

### Post by finer recliner on 2008-04-03
from [http://www.psychocats.net/ubuntu/installingsoftware#source](http://www.psychocats.net/ubuntu/installingsoftware#source):

```

sudo aptitude update
sudo aptitude install build-essential

```

the build-essential package includes gcc, g++ and some other stuff. this is what you need.


anything you install from the repositories (i.e. using apt-get or synaptec), comes pre-compiled for a quick and easy installation.

enjoy!

---

### Post by choben on 2008-04-03
build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: g++ but it is not going to be installed
 Depends: dpkg-dev but it is not going to be installed

=\

---

### Post by choben on 2008-04-03
well now I'm using aptitude as you suggested
...forgive my potential ignorance.

---

