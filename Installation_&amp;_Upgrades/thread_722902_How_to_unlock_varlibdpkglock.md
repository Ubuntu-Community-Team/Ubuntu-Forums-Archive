---
title: "How to unlock /var/lib/dpkg/lock"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by garloosh on 2008-03-12
When i tried installing java or wine on Ubuntu 7.10 i keep getting the same unlock error. Below is the error i got when i tried installing java

garloosh@garloosh-laptop:~$ sudo apt-get install sun-java6-plugin
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Is there a setting i need to change to allow the install?

thanks,

---

### Post by jrusso2 on 2008-03-12
Do you have synaptic or add remove programs open when you run apt?  If you do you get that message.

---

### Post by garloosh on 2008-03-12
No, i just have the terminal running

---

### Post by erginemr on 2008-03-13
Please follow this thread:
[http://ubuntuforums.org/showthread.php?t=631128&highlight=lock](http://ubuntuforums.org/showthread.php?t=631128&highlight=lock)
If it doesn't work, try this one:
[http://ubuntuforums.org/showthread.php?t=709160&highlight=lock](http://ubuntuforums.org/showthread.php?t=709160&highlight=lock)

---

