---
title: "Getting GGZ working in 10.10"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by andru183 on 2010-11-19
Hey guys, I having trouble getting GGZ to start in 10.10, I have it installed as of [http://packages.ubuntu.com/maverick/ggz](http://packages.ubuntu.com/maverick/ggz)
and when I try to run ggzd I get

(<errorsys>) Unable to read file /etc/ggzd/ggzd.conf: No such file or directory
(<errormsg>) WARNING:  No configuration file loaded!

In the man pages all the links to configure point to files that don't exist.

What the hell am I doing wrong??

---

### Post by Zookalicious on 2010-11-19
Hey andru183, it is possible that your installation did not complete, or was interrupted somehow. If you appear to be missing files I would suggest that you uninstall the application and then reinstall it through the Ubuntu Software Center, or by typing 
```

sudo apt-get install ggz

```

In the terminal. 

Let me know where that gets you or if you have any questions :D

---

### Post by andru183 on 2010-11-19
thanks for the advice, alas, nope, 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ggz is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

and it still won't launch, I've uninstalled and retried, I'm actually stumped

---

### Post by Zookalicious on 2010-11-19
Odd, you've installed both ggz and ggzd correct?

---

### Post by andru183 on 2010-11-20
yep, everything in the synaptic manager cept the dev library's, is there some way to create the missing file and copy someone elses contents??

---

