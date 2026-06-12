---
title: "how to install sun-java6 on ubuntu lucid"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by a.tawila on 2010-08-30
hi, i'm just migrated to ubuntu lucid from windows 7, and i need to install sun-java6.
i've tried to install it many ways but failed.
1- first, i tried using the ubuntu software center, but i got a failure message as in the next screenshoot 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=167931&stc=1&d=1283158477[/IMG]

2- i tried to install it from the shell:
```
sudo apt-get install sun-java6-bin
```but got the following:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc but it is not installable
E: Broken packages
```i figured out that i need to install unixodbc first, but when i tried
```
sudo apt-get install unixodbc
```i got
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unixodbc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unixodbc has no installation candidate
```:confused:

so, anyone can give a hint or something useful. this will be really appreciated.
thank you.

---

### Post by Mze on 2010-08-30
Check Ubuntu Geek's [tutorial]("http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html")

---

### Post by oldos2er on 2010-08-30
Have you run ```
sudo apt-get update
``` recently?

---

