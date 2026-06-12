---
title: "oracle-java7-installer blocks all other APT activity"
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by borepstein on 2012-06-11
Hello all,

Tried to install oracle-java7-installer, that went nowhere. OK, no problem. But now I can not uninstall it and no other packages would install. That is on Ubuntu 12.04LTS.

I tried "sudo apt-get clean" - but that doesn't help. Is there a more radical way to get my dpkg database into a manageable state?

Thanks.

Boris.

---

### Post by mojohn on 2012-06-12
Boris, I'm having the same problem. Hopefully, someone will help us out soon!

mojohn

---

### Post by QIII on 2012-06-12
What happened and what error messages did you get?  What exactly is happening when you attempt to install new packages?

Where did you get the package and what is the link to the instruction?  Were instructions for uninstalling included?

What exactly did you attempt to do to uninstall it?

---

### Post by Curtis6767 on 2012-06-12
When you get all this sorted out, you might want to look at these sites. If you're already aware of these sites, followed the instructions there, and still met with failure, then my apologies.

Look each site over first before doing anything.

[https://launchpad.net/~webupd8team/+archive/java](https://launchpad.net/~webupd8team/+archive/java)

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by mojohn on 2012-06-12
Did some more research. The instructions at:

[http://askubuntu.com/questions/121226/how-to-completely-remove-a-oracle-jdk-that-didnt-install-properly](http://askubuntu.com/questions/121226/how-to-completely-remove-a-oracle-jdk-that-didnt-install-properly)

worked for me.

mojohn

---

