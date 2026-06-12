---
title: "[SOLVED] Splunk wont install on regular ubuntu"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by datakid on 2007-11-04
Hola, 

On a fully updated Gutsy...

I downloaded the Splunk tgz and followed the instructions - I un tgz'd to /opt/ and etc.

When I run

boxen:$sudo /opt/splunk/bin/splunk start

to start the plunk server for the first time I get the following:


```
This appears to be your first time running Splunk.
/bin/sh: Can't open python
/bin/sh: Can't open python

/opt/splunk/var does not exist. Will create
/opt/splunk/var/log does not exist. Will create
/opt/splunk/var/log/splunk does not exist. Will create
/opt/splunk/var/run does not exist. Will create
/opt/splunk/var/run/splunk does not exist. Will create
/opt/splunk/var/spool does not exist. Will create
/opt/splunk/var/spool/splunk does not exist. Will create
/opt/splunk/var/spool/dirmoncache does not exist. Will create
/opt/splunk/var/lib does not exist. Will create
/opt/splunk/var/lib/splunk does not exist. Will create
/opt/splunk/var/lib/splunk/authDb does not exist. Will create
/opt/splunk/var/lib/splunk/hashDb does not exist. Will create
/bin/sh: Can't open python

/bin/sh: Can't open btool
/bin/sh: Can't open btool
Checking prerequisites... 
Checking mgmt port []: open
Port conflicts with http port.
Would you like to change ports? [y/n]: y
Enter a new mgmt port: 8888
Setting mgmt to port: 8888
/bin/sh: Can't open python

```


I can type /bin/sh and get a shell, I can type python at that shell prompt and get a python shell prompt, but I can't install splunk? I just keep getting this over and over:

```

Would you like to change ports? [y/n]: y
Enter a new mgmt port: 8888
Setting mgmt to port: 8888
/bin/sh: Can't open python

```

I've tried with ports 8088, 1000, 9000, all weird number I knew were empty, but nothing....

Any ideas?

---

### Post by datakid on 2007-11-04
Problem discovered/solved. <redface>The 64 bit tgz wont install on a 32 bit CPU</redface>

---

