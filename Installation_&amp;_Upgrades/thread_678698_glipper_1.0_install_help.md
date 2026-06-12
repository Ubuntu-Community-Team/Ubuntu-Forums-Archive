---
title: "glipper 1.0 install help"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by martynp on 2008-01-26
Hi,

I am trying to install the latest version of glipper and it does not have a .deb and neither is it in the repos.

I have downloaded and extracted the source, read the instructions and tried to configure using:

./configure --prefix=/usr --with-gconf-schema-file-dir=/usr/share/gconf/schemas

as instructed in the readme. I get the following error at the end of the config run:

checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

and am then unable to make which gives the following error:

make: *** No targets specified and no makefile found. Stop.

I have made and installed other apps from source so believe I have all the right dependencies.

Could anyone shed some light as I have run out of ideas. I am running gutsy with all the latest updates.

Many Thanks in advance

---

### Post by harold4 on 2008-01-26
```
sudo apt-get install python-dev
```

---

### Post by martynp on 2008-01-26
Many thanks for the quick reply....

After doing what you posted it still required another package but after that all installed ok

Thanks again

---

