---
title: "Out of sync installations...."
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by tituspurdin on 2011-03-18
I have several (5) machines running various flavors of Ubuntu.  One
of them does not have Java on it (jre or jdk).  I don't know why it
doesn't; but it doesn't.  No big deal.  Fire up synaptic and load it
up.  Oops.  Dependency problems.  And when I drill down, there is a
base dependency on 'tzdata'.  The dependency message is:

tzdata-java: Depends: tzdata (= 2010i-1) but 2010o-0ubuntu0.10.04
is to be installed

Having Java on that machine is not critical.  It is on all of the
others.  But I would like to get this straightened out.  Appreciate
what help I can dredge up.  Thanks.


Titus sends

---

### Post by Old_Grey_Wolf on 2011-03-18
You can use the following command to fix the dependency problem.
```
sudo apt-get -f install
```

You will need to install JAVA JRE from the repos if you what it. To install the current the Sun JAVA JRE for 10.04 enter this command.```
sudo apt-get install gsfonts-x11 java-common odbcinst1debian1 sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin unixodbc odbcinst
```

---

