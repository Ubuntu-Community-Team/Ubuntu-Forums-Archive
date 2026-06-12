---
title: "i dont know why its occuring"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by raja.genupula on 2011-07-18
```
sudo apt-get install thunderbird
'E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

i am getting this ...please help me . i am sure no other application installing .

                                                   thanks advance

---

### Post by dino99 on 2011-07-18
you may not use several ways to install/update at once: only one can be used at time

---

### Post by raja.genupula on 2011-07-18
dino i am sure man .
i have started the installation ,  after that my net disconnected . so i had stopped that installation by using ctrl+z . after i have connected my net and then i have typed the above command and got the  error .

---

### Post by raja.genupula on 2011-07-18
man , just now i executed that  and got that  
 ```
sudo dpkg --configure -a
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up thunderbird (3.1.11+build2+nobinonly-0ubuntu0.11.04.1) ...
Processing triggers for python-support ...
assassin@genupulas:~$ sudo apt-get install thunderbird
Reading package lists... Done
Building dependency tree       
Reading state information... Done
thunderbird is already the newest version.
The following packages were automatically installed and are no longer required:
  libgfortran3 xulrunner-2.0 python-numeric python-utidylib python-gtkmozembed
  python-beautifulsoup libtidy-0.99-0 python-numpy python-tz
  xulrunner-2.0-mozjs python-feedparser python-rsvg python-dateutil libblas3gf
  liblapack3gf python-evolution
```


any ways problem solved , but still i dont why that has occurred ? 
thank you for your response man .

---

### Post by dino99 on 2011-07-18
sudo apt-get autoremove

---

### Post by raja.genupula on 2011-07-18
are you sure that no problems will rise

---

### Post by raja.genupula on 2011-07-18
i have downloaded 150mb of updates out of 200mb. i am facing problem with update-bug 
so  i am afraid  that  downloaded 150mb will be erased if i run apt-get autoremove...was it gone if i did autoremove ?

---

### Post by raja.genupula on 2011-07-20
what ever i am done with the issue

---

