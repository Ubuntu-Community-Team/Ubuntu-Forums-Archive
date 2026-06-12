---
title: "error msg when trying to install with synaptic"
date: 2006-02-26
forum: Installation &amp; Upgrades
---

### Post by risknothin on 2006-02-26
i get this error when im trying to install...

E: gaim: subprocess post-installation script returned error exit status 1

what does that mean? gaim isnt even running

---

### Post by ape on 2006-02-26
This error means that you are trying to installl gaim (or have attempted to install it in the past) and the /var/lib/dpkg/info/gaim.postinst script has an error in it. (this script is run after unpacking the gaim .deb file).  From the command prompt try running `sudo apt-get install gaim` and see what the actual error message from that script is.  Hopefully there will be a line number for the script and you can take a look at what is actually being attempted by the script.

---

### Post by risknothin on 2006-02-26
it installs however i get this error

rmdir: `/usr/share/doc/gaim': Directory not empty
dpkg: error processing gaim (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gaim
E: Sub-process /usr/bin/dpkg returned an error code (1)


what does that mean?

---

### Post by risknothin on 2006-02-26
no one knows how i can fix this?  

This is the problem, when i have gaim installed, every other program i install has this error and when i remove gaim then the error goes away.  can i fix this? i like gaim more then other clients.  Unless there is a better one.

---

### Post by Xian on 2006-02-26
[QUOTE=risknothin]rmdir: `/usr/share/doc/gaim': Directory not empty[/QUOTE]

Since it complains about the dir not being empty...try emptying it.
For some reason it appears the script is failing at this point.

---

