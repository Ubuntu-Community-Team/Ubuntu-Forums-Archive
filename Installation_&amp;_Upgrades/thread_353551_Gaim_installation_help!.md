---
title: "Gaim installation help!"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by Ritchstorm on 2007-02-04
I am trying to install gaim 1.5.0 from source. I am installing from source so that I can later install xfire plugin with messing around with the configuration. I am running 6.10 as root. I type ./configure and all goes well. I then try make. I get this error 

```
../libtool: line 1799: cd: NONE: No such file or directory
libtool: link: cannot determine absolute directory name of `NONE'
make[3]: *** [gaim] Error 1
make[3]: Leaving directory `/home/ritchstorm/gaim-1.5.0/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ritchstorm/gaim-1.5.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ritchstorm/gaim-1.5.0'
make: *** [all] Error 2
```

Can anyone help me?! Many thanks in advance!

---

### Post by phossal on 2007-02-05
You probably want to run those commands with *sudo*. Plus, make sure you've installed build-essential. 
```
sudo apt-get install build-essential
sudo *make*
```

---

