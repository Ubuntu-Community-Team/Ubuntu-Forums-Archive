---
title: "Java 1.5"
date: 2005-05-07
forum: Installation &amp; Upgrades
---

### Post by Me_Titus on 2005-05-07
Hi there,

Most important then anything I am a totally newbie in the Linux world.


I have installed ubuntu recently, and i recently started installed other stuff that i frequently use on windows, like eclipse.
I had no problem installing eclipse, but when it came the time to install java, i came to a nightmare.

Well i  fallowed every step from here ([http://wiki.osuosl.org/display/dev/java+on+debian](http://wiki.osuosl.org/display/dev/java+on+debian))
I am sure you all know what steps i am talking about.
 
But when i reached this bit:

[INDENT]cd /var/install/java
mkdir pkg
cd pkg
cp /usr/share/doc/java-common/dummy-packages/*.control /var/install/java/pkg/
equivs-build java-compiler-dummy.control
equivs-build java-virtual-machine-dummy.control
equivs-build java2-runtime-dummy.control
equivs-build java2-compiler-dummy.control[/INDENT]

i got into some problems. Firstful i dont have this directory on my system
".../java-common/dummy-packages/"
so i went and got the control files from the debian website instead. I now have the *.control files but when i do 

[INDENT]equivs-build java-compiler-dummy.control[/INDENT]

It says that the command cannot be found.

Can anyone help me with this.

Many thanks,

Marco

---

### Post by bonifacio on 2005-05-08
you should be following the guide in [http://ubuntuguide.org/](http://ubuntuguide.org/) for a less painful way in installing java

---

### Post by Me_Titus on 2005-05-08
[QUOTE=bonifacio]you should be following the guide in [http://ubuntuguide.org/](http://ubuntuguide.org/) for a less painful way in installing java[/QUOTE]

And think that i've lost one day on those debian forums.
MANY THANKS MATE.


 :-)  :-)  :-)  :-)  :-)  :-)  :-)

---

