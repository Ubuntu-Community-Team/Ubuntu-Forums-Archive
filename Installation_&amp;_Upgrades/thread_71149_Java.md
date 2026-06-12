---
title: "Java?"
date: 2005-10-02
forum: Installation &amp; Upgrades
---

### Post by augereffect on 2005-10-02
I'm trying to install java, the one that you used to be able to get by typing this:
apt-get install sun-j2sdk1.5 sun-j2sdk1.5debian
Could someone guide me through how to download the thing and make the deb?

---

### Post by swerner on 2005-10-02
[QUOTE=augereffect]I'm trying to install java, the one that you used to be able to get by typing this:
apt-get install sun-j2sdk1.5 sun-j2sdk1.5debian
Could someone guide me through how to download the thing and make the deb?[/QUOTE]
Try this thread, it's got some information on what you are looking for:
[http://ubuntuforums.org/showthread.php?t=655](http://ubuntuforums.org/showthread.php?t=655)

---

### Post by psylvester on 2005-10-03
root@ubuntu:/home/sylvu # apt-get install sun-j2sdk1.5 sun-j2sdk1.5debian
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2sdk1.5
root@ubuntu:/home/sylvu #

please help to install JAVA.

thanks.

---

### Post by codejunkie on 2005-10-03
[QUOTE=psylvester]root@ubuntu:/home/sylvu # apt-get install sun-j2sdk1.5 sun-j2sdk1.5debian
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2sdk1.5
root@ubuntu:/home/sylvu #
please help to install JAVA.
thanks.[/QUOTE]
the java package was removed from the backports repo because of copyright restrictions, but bored2k has written as easy to follow guide on how to install java by creating your own java .deb package [http://ubuntuforums.org/showthread.php?t=70428](http://ubuntuforums.org/showthread.php?t=70428) all the credit goes to him.

---

