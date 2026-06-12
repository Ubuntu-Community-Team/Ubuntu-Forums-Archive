---
title: "gcc install on a command line environment"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by yvesp on 2011-02-26
I installed a command line version of Ubuntu 10.10 using the alternate install disk. To suit my needs, I have to install the gcc C compiler in this environment. When connected under root, I enter the command: 'apt-get install gcc'. The error 'E: unnable to locate package gcc' is then displayed on screen.
 
Can you tell how to install gcc? Is this package available from the alternate install disk or do we have to download it. If I dowbload a tar file, where should I copy it to to be able to have the install application see it?
 
Thank you, Yves Plasse.

---

### Post by Frogs Hair on 2011-02-26
This may helpful . [http://tigcc.ticalc.org/doc/comopts.html](http://tigcc.ticalc.org/doc/comopts.html)

---

### Post by oldos2er on 2011-02-26
The build-essential package will get you gcc basics. If you need more, run **apt-cache search gcc** and you will get many choices.

---

