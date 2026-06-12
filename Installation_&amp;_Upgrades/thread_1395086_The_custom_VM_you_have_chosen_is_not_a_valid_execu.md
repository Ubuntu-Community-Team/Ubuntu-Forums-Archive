---
title: "The custom VM you have chosen is not a valid executable."
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by li_bi on 2010-01-31
Hello

I installed eclipse followng these steps:

```
sudo apt-get install eclipse sun-java6-jdk
sudo update-java-alternatives -s java-6-sun
  sudo -b gedit /etc/java-6-sun/jvm.cfg

```and add the following to the top of the file

```
/usr/lib/jvm/java-6-sun
```Then, I opened this file:
```
sudo -b gedit /etc/eclipse/java_home
```and added

```
/usr/lib/jvm/java-6-sun
```to the top of the file.


When I type $eclipse from the terminal I get: using specified vm: /usr/lib/jvm/java-6-sun-1.6.0.06


In my /usr/lib/jvm/ I only have the following: java-1.5.0-gcj-4.3-1.5.0.0 ; java-6-sun; java-6-sun-1.6.0.16 and java-gcj. So no java-6-sun-1.6.0.06.


In the file: /etc/eclipse/java_home I have as first line /usr/lib/jvm/java-6-sun
In my /etc/profile  file I have : export JAVA_HOME="/usr/lib/jvm/java-6-sun"
And in my /etc/java-6-sun/jvm.cfg file I have also /usr/lib/jvm/java-6-sun

I ran out of options and really don't know where the problem might be. 

Thanks.

---

