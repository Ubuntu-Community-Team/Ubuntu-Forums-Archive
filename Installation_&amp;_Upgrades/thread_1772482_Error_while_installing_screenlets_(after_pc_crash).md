---
title: "Error while installing screenlets (after pc crash)"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by volto on 2011-05-31
Hello,
I am an absolute beginner, and I have a  problem:


While I was installing screenlets via

```
sudo apt-get install screenlets
```My pc restarted due to electricity cut off! and now when I try to re-install I get that error in terminal

```
dpkg: error processing python-numpy (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 man-db
 liblapack3gf
 python-numpy
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by jerrrys on 2011-05-31
this may help

[http://ubuntuforums.org/showthread.php?t=1367582](http://ubuntuforums.org/showthread.php?t=1367582)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Sub-process+%2Fusr%2Fbin%2Fdpkg+returned+an+error+code+%281%29&as_qdr=all&sa=Google+Search&lang=en#881](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Sub-process+%2Fusr%2Fbin%2Fdpkg+returned+an+error+code+%281%29&as_qdr=all&sa=Google+Search&lang=en#881)

---

### Post by volto on 2011-05-31
Thanks for the reply jerrys,

I ran:
```
sudo dpkg --configure -a
```

and I got this output:

```
Errors were encountered while processing:
 man-db
 libpam0g
 liblapack3gf
 python-numpy
```

---

### Post by volto on 2011-05-31
SOLVED! here is what I have done:


Opened terminal and  

```
cd /var/lib/dpkg/info
```

then

 ```
sudo rm man-db.* 
 sudo rm libpam0g.*  
sudo rm liblapack3gf.* 
 sudo rm python-numpy.* 

```

After wards I did

```
sudo apt-get install screenlets
```
And it worked like charm

---

