---
title: "When launching update manager I recieve the following message - how do I correct"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by rupert52 on 2008-05-02
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package sn9cxxx needs to be reinstalled, but I can't find an archive for it.'

---

### Post by agim on 2008-05-02
According to the Google, that package is something used for webcams. Is that true? Are you using a webcam? It will help to pinpoint the problem.

---

### Post by rupert52 on 2008-05-18
The snc9xxx driver is for a webcam - I was trying to install it but gave up. Now I am unable to use update manager.  I am running ubuntu 7.04 and would like to update. I can't work uot how to uninstall the driver to get it out of the system.

---

### Post by unicorn_2003_1 on 2008-06-07
bumper.

Having a similar "needs to be reinstalled, and find an archive for it" error.

someone help!

---

### Post by zvacet on 2008-06-08
@ **rupert52**

```
sudo apt-get --purge remove packagename
```

or 

```
sudo dpkg --remove --force-remove-reinstreq packagename
```

@ **unicorn_2003_1**

Same for you,but if you want to keep package try with 

```
sudo apt-get install --reinstall packagename
```

---

