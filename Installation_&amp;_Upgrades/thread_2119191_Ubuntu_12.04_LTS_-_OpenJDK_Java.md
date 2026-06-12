---
title: "Ubuntu 12.04 LTS - OpenJDK Java"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by MakeMakeMake on 2013-02-23
Hi, today I wanted to remove "OpenJDK Java 7 Runtime" in the Software Center. 

But once I remove "OpenJDK Java 7 Runtime" it would automatically also install "OpenJDK Java 6 Runtime" and "IcedTea Java Web Start".   

When I remove "OpenJDK Java 6 Runtime" (and "IcedTea Java Web Start") there will be automatically "OpenJDK Java 7 Runtime" installed. 

What can I do?

---

### Post by x64Architecture on 2013-02-23
Try running these commands in the terminal:

```
sudo apt-get update 
apt-cache search java | awk '{print($1)}' | grep -E -e '^(ia32-)?(sun|oracle)-java' -e '^openjdk-' -e '^icedtea' -e '^(default|gcj)-j(re|dk)' -e '^gcj-(.*)-j(re|dk)' -e 'java-common' | xargs sudo apt-get -y remove 
sudo apt-get -y autoremove
```   Purge config files:
  ```
dpkg -l | grep ^rc | awk '{print($2)}' | xargs sudo apt-get -y purge
```   Remove Java config and cache directory:
  ```
sudo bash -c 'ls -d /home/*/.java' | xargs sudo rm -rf
```   Remove manually installed JVMs:
  ```
sudo rm -rf /usr/lib/jvm/*
```   Remove Java entries, if there is still any, from the *alternatives*:
  ```
for g in ControlPanel java java_vm javaws jcontrol jexec keytool mozilla-javaplugin.so orbd pack200 policytool rmid rmiregistry servertool tnameserv unpack200 appletviewer apt extcheck HtmlConverter idlj jar jarsigner javac javadoc javah javap jconsole jdb jhat jinfo jmap jps jrunscript jsadebugd jstack jstat jstatd native2ascii rmic schemagen serialver wsgen wsimport xjc xulrunner-1.9-javaplugin.so; do sudo update-alternatives --remove-all $g; done
```   Search for possible remaining Java directories:
  ```
sudo updatedb sudo locate -b '\pack200'
```   If the command above produces any output like **/path/to/jre1.6.0_34/bin/pack200** remove the directory that is parent of **bin**, like this: sudo rm -rf /path/to/jre1.6.0_34.

Taken from: [http://askubuntu.com/questions/84483/how-to-completely-uninstall-java](http://askubuntu.com/questions/84483/how-to-completely-uninstall-java)

---

