---
title: "Reinstall from cd?"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by ralphwiggum on 2010-08-05
After upgrading to 10.04 my system failed to boot properly.  I attempted to fix this and had to run a file system check on my hard drive to repair it.  This broke my system so I am no longer able to run commands such as apt-get from the terminal or from the rescue prompt.  My files are intact but some os ones are missing.
I have the live cd and alternate cd but was not able to find an option to reinstall without formatting my partition.  Is there a way to reinstall the os without losing my data or am I forced to do a clean install?

---

### Post by bschelst on 2010-08-05
question:  do you have the dpkg command?
If so, maybe it's enough to install the apt-get package..

---

### Post by ralphwiggum on 2010-08-05
No, that was also broken.
In the terminal I keep getting the error 
-bash: /usr/bin/python: No such file or directory
or bad interpreter
so there is probably something wrong with my shell which is why I was trying to use the cd.

---

### Post by ralphwiggum on 2010-08-05
I lost my /usr/bin directory somehow so I copied the live cd and it seems to have fixed it.

---

