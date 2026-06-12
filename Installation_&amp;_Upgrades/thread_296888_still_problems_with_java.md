---
title: "still problems with java"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by doh224 on 2006-11-10
hi all. again! I really need some help. I really don't understands this, I've asked for help before. and I think I've followed the instruktions pretty well. 

Well here's the deal. I've installed this run time java that should make me abel to play java games on the internet. It should be installed, but every time I tries to play a game it shows nothing. usually, the web site would say that you're missing a plugin with java, but it don't. there's just a white blank scheen where the game were supossed to be? can anybody help me with that? I would really appressiate the help? 

:confused:

---

### Post by doh224 on 2006-11-10
why does things like these never get answerred :(

---

### Post by taurus on 2006-11-10
How did you install java on your system?  Open a terminal, Applications -> Accessories -> Terminal, and paste output of this command here...

```
java -version
```

---

### Post by doh224 on 2006-11-10
java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.




that what it says when it type the command.

---

### Post by taurus on 2006-11-10
Sorry but that is the wrong version!!!  In other words, it's a wannabe so you need to install an actual version from either Sun or Blackdown.  And of course, you can use automatix to install it so just follow the instructions on this page...

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by zadax on 2006-11-11
First, update your java to 1.5 - most sites use this version these days.  You can get it from ubuntu via the synaptic software managers (enable multiversal software).  Install "sun java" packages.

If that doesn't work for you you can try to these directions to install the version downloaded from sun.java.com
[http://www.ubuntuforums.org/showthread.php?t=297770](http://www.ubuntuforums.org/showthread.php?t=297770)

Then follow these instructions to get the plugin to work (mind you firefox is mozilla):
[http://java.sun.com/j2se/1.5.0/manual_install_linux.html](http://java.sun.com/j2se/1.5.0/manual_install_linux.html)

HTH

---

### Post by doh224 on 2006-11-12
thanks. :) it was a little deficult that explanation. but thanks! I got it working!

---

### Post by jonesyp on 2006-11-12
Can someone explain the Java version numbers?  On Java.com the version number is 5.0 Update 9, but the Automatix software mentions 1.5?  Is it a different piece of software?  Thanks

---

