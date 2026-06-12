---
title: "update manage not working"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by rbouch2010 on 2010-10-05
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 20000000. (man 5 apt.conf), E:Error occurred while processing libcgi-untaint-perl (NewFileDesc2), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

went to the terminal and used "sudo apt-get update" as well as "sudo apt-get dist-upgrade" both error out following error message for dist-upgrade:

E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 20000000. (man 5 apt.conf)
E: Error occurred while processing libcgi-untaint-perl (NewFileDesc2)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages
W: Unable to munmap
E: The package lists or status file could not be parsed or opened.

---

### Post by mörgæs on 2010-10-05
Hi, welcome to the forum. 

Since you are running Ubuntu 9.04, which is unsupported by the end of the month, it is best to forget all about solving the error and in stead install 10.04.

---

### Post by rbouch2010 on 2010-10-05
I am running 10.04, as per "System->About Ubuntu". Don't really see where it said I was running 9.04 but if I gave the impression I was running 9.04 then I'm sorry.

---

### Post by mörgæs on 2010-10-05
The error message talks about 'jaunty', so there is some 9.04 cruft on the machine making trouble.

---

### Post by rbouch2010 on 2010-10-05
Alright, thanks for the info, just commented out the jaunty stuff in sources.list and everything began to work again! Once again, thanks for the info.

---

### Post by coffeecat on 2010-10-05
You might find:

```
sudo apt-get autoclean
```

.. useful. It could be that the apt cache is overfull. Certainly it would clear out any old Jaunty packages that might be hanging around taking up space.

---

### Post by rbouch2010 on 2010-10-05
Will try that once I finish the current install.

---

