---
title: "Getting permission to add files to the /etc and /usr directories"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by dbsoundman on 2007-08-15
I have a program (powerd) that I need to insert elements of into the /usr and /etc directories in order for it to work. The main thing I need to put in the /etc directory is a config file. There are of course others that I think I could run from where they are now (home directory), but it would be "cleaner" to put them in the right place. I can't figure out how to get permission to do this, though. Any tips?

Also, does this look like a correct .conf file?
> 
#
#.config
#
#MODE monitor
#MONITOR /dev/ttyS0
#POWERFAIL CTS LOW
#DELAY 16


Thanks,
Dan

---

### Post by Pumalite on 2007-08-15
sudo chmod 777 /usr
sudo chmod 777 /etc

When you are done:
sudo chmod 000 /usr
sudo chmod 000 /etc

---

### Post by aysiu on 2007-08-15
> **Pumalite said:**
> sudo chmod 777 /usr
sudo chmod 777 /etc

When you are done:
sudo chmod 000 /usr
sudo chmod 000 /etc
Changing permissions on system directories is a quick way to break your system. I highly advise against doing so.

If you have a GUI, just [launch the file browser with root privileges](http://www.psychocats.net/ubuntu/permissions#gui).

If you are operating a GUI-less server (command-line only), use *sudo* to create the config file: ```
sudo nano /etc/powerd/powerd.conf
``` for example.

---

