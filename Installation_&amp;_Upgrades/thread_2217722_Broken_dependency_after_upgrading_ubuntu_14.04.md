---
title: "Broken dependency after upgrading ubuntu 14.04"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by vish garg on 2014-04-18
I recently upgraded to ubuntu 14.04 LTS but few packages are broken. I  tried to run the command apt-get -f install and dpkg --configure -a but  nothing worked for me. Please help ..

---

### Post by Bashing-om on 2014-04-18
vish garg; Hi !

Feel for you. Post back - between code tags - the out puts of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

To show us what is and someone will advise on a corrective action.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by vish garg on 2014-04-19
Actually there was a problem in a package, I remoed that package and now its working fine. Thanks for the help :)

---

### Post by father_ted on 2014-04-19
There seem to be issues with libpostproc52_6 which are stopping some apt-get upgrade attempts.

---

### Post by vish garg on 2014-04-20
you are right and there are problems like I was watching video on ubuntu and after few minutes the screen was going to lock I simply dragged mouse the screen was freezed and I was only able to hear sound. Then, I was forced to restart my pc. I think there was a problem with lock screen.

---

