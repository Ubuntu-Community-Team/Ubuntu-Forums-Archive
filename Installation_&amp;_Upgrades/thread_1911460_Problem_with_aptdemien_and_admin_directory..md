---
title: "Problem with aptdemien and admin directory."
date: 2012-01-18
forum: Installation &amp; Upgrades
---

### Post by pawtracks on 2012-01-18
There is a problem with aptdemeion and the lock file? Need some help. Unable to install anything. :confused:

pawtracks@ubuntu:~$ sudo apt-get install
[sudo] password for pawtracks: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Edit: Answer for this problem can be found on this post: [http://ubuntuforums.org/showthread.php?t=1911838](http://ubuntuforums.org/showthread.php?t=1911838)

---

### Post by qhaz on 2012-01-19
Greetings.  I am experiencing the same problem and error message.  I'm trying to upgrade from 11.04 natty to 11.10 oneiric. Anyone able to shed some light on this problem?

---

### Post by oldos2er on 2012-01-19
> **pawtracks said:**
> There is a problem with aptdemeion and the lock file? Need some help. Unable to install anything. :confused:

pawtracks@ubuntu:~$ sudo apt-get install
[sudo] password for pawtracks: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Only one package manager can be open at a time. Do you have Software Center or Synaptic open?

---

### Post by cortman on 2012-01-19
> **pawtracks said:**
> There is a problem with aptdemeion and the lock file? Need some help. Unable to install anything. :confused:

pawtracks@ubuntu:~$ sudo apt-get install
[sudo] password for pawtracks: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Currently answering that question in [this thread]("http://ubuntuforums.org/showthread.php?t=1911838").

---

### Post by pawtracks on 2012-01-22
> **cortman said:**
> Currently answering that question in [this thread]("http://ubuntuforums.org/showthread.php?t=1911838").

Thanks for the answer.

---

