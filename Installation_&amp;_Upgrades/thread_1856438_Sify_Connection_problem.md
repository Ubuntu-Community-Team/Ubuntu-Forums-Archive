---
title: "Sify Connection problem"
date: 2011-10-08
forum: Installation &amp; Upgrades
---

### Post by mihir.khatwani on 2011-10-08
I installed the new sifyconnect dialer downloaded from their site.
The installation was successful but whenever I try to access the dialer it gives me this error.
Ubuntu 10.04.1 :D

```
sudo sifyconnect
sudo: unable to execute /usr/bin/sifyconnect: No such file or directory

```while the file is present in the usr/bin directory.

```
root@mihir:/usr/bin# find sifyconnect
sifyconnect
root@mihir:/usr/bin# 

```What should I do now?

---

### Post by raja.genupula on 2011-10-08
Hi have you tried this .
[http://broadbandforum.in/sify-broadband/7062-install-sify-bb-ubuntu-linux/](http://broadbandforum.in/sify-broadband/7062-install-sify-bb-ubuntu-linux/)

---

### Post by mihir.khatwani on 2011-10-09
Yes sir, I have tried that, and other other tutorial available via google.
I have also tried 
ln -s /usr/bin/sifyconnect sifyconnect
and different variations of the above code.

---

### Post by raja.genupula on 2011-10-09
Hi i think in your tar file there will be a README file . i think that gonna help you to proper install and to proper usage.

you said you have installed right!
please check the output of 
```
which <your apps name>
``` in the terminal.

all the best

---

