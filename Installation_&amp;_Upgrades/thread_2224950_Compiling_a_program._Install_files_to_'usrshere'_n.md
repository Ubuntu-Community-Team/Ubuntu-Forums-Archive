---
title: "Compiling a program. Install files to '/usr/shere/' not /usr/local/share'"
date: 2014-05-19
forum: Installation &amp; Upgrades
---

### Post by J_Me on 2014-05-19
Can you specify a destination folder e.g. '/usr/shere/' rather than /usr/local/share' when compiling/installing a program with './configure, make, make install'.
I can give you more details of what I'm trying to do if needed.
Thanks

---

### Post by steeldriver on 2014-05-19
It depends I think - in my experience most source distributions using autoconf (./configure script) support a **--prefix** parameter to set the *root* of the install location (e.g. --prefix=/opt or --prefix=/usr instead of /usr/local), but whether there is fine control over installation of particular subcomponents is a more hit and miss. By convention, if you run 

```
./configure --help
```

it should list the available parameters / options for your particular source package.

---

### Post by J_Me on 2014-05-20
Thanks for pointing me in the right direction steeldriver.

---

### Post by monkeybrain20122 on 2014-05-20
```
./configure --prefix=/usr
```

You may also want to use checkinstall instead of make install. it creates a .deb so after installation you will find your package in the software management system (e.g synaptic) instead of scattering all over the file system. That way it is easy to keep track and remove (in case you need to)
checkinstall needs to be installed from repo

```
sudo apt-get install checkinstall
```

so the procedure would now be
```
./configure --prefix=/usr
make 
sudo checkinstall

```

---

### Post by J_Me on 2014-05-21
@monkeybrain20122
Thanks for the clear and concise explanation

---

