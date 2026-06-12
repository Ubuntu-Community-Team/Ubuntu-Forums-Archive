---
title: "Upgrade from 12.10 to 13.04 fails and apt problem"
date: 2013-07-05
forum: Installation &amp; Upgrades
---

### Post by axept on 2013-07-05
When trying to upgrade my release from 12.10 to 13.04 I get this output in terminal:

  
```
axept@aXept-Lifebook:~$ sudo do-release-upgrade 
Ser etter ny utgave av Ubuntu 
Traceback (most recent call last):   File "/usr/bin/do-release-upgrade", line 144, in <module>    
 fetcher = get_fetcher(options.frontend, m.new_dist, options.data_dir)  
 File "/usr/bin/do-release-upgrade", line 37, in get_fetcher    
 from DistUpgrade.DistUpgradeFetcherCore import DistUpgradeFetcherCore   
File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcherCore.py",       line  30, in <module>   
 import tempfile EOFError: EOF read where not expected Error in sys.excepthook: 

Traceback (most recent call last): File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 64, in             
 apport_excepthook from apport.fileutils import likely_packaged, get_recent_crashes 
File "/usr/lib/python3/dist-packages/apport/__init__.py", line 4, in <module> from apport.report import 
Report File "/usr/lib/python3/dist-packages/apport/report.py", line 12, in <module> import subprocess, tempfile, os.path, re, pwd, grp, os 
EOFError: EOF read where not expected  Original exception was: 
Traceback (most recent call last): 
 File "/usr/bin/do-release-upgrade", line 144, in <module>  fetcher = get_fetcher(options.frontend, m.new_dist, options.data_dir) 
 File "/usr/bin/do-release-upgrade", line 37, in get_fetcher  from DistUpgrade.DistUpgradeFetcherCore import DistUpgradeFetcherCore  
 File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcherCore.py", line      30, in <module>  import tempfile 
EOFError: EOF read where not expected 
axept@aXept-Lifebook:~$
```   

And when running apt-cache info:

```
axept@aXept-Lifebook:~$ apt-cache policy ubuntu-release-upgrader-core
 ubuntu-release-upgrader-core:
 Installert: 1:0.190.7 
Kandidat:   1:0.190.7 
Versjonstabell: *** 1:0.190.7 0     

500 http://no.archive.ubuntu.com/ubuntu/ quantal-updates/main amd64 Packages     
500 http://gb.archive.ubuntu.com/ubuntu/ quantal-updates/main amd64 Packages     
500 http://security.ubuntu.com/ubuntu/ quantal-security/main amd64 Packages     
100 /var/lib/dpkg/status  1:0.190.1 0     
500 http://no.archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
```   

And:

  
```
sudo apt-get update && sudo apt-get upgrade
```   

Don't do anything. All is up to date apparently..

  Trying to launch "Update Manager" gives the same error as "do-release-upgrade". Tried to remove .pyc files in /etc/apt/dist-packages/ and reinstalled python stuff as found in a Bug-report...

  
Any suggestion? 

  
Btw, running "Software packages" from "system-settings" doesn't work.  It won't start. Suppose its the same reason.. Its been slow to start  before, but now it just won't start.

  

I also get this error when trying to add a repository from terminal.. Whats going on??????

---

### Post by dino99 on 2013-07-05
open /etc/apt/sources.list, and change "quantal" by "raring", and deactivate third party repos if any, like ppa(s)
save and close that file, then update/upgrade again

note: think to clean the system before doing the above commands: clean/autoclean/autoremove/gtkorphan/bleachbit

---

### Post by axept on 2013-07-06
And where should I disable third party repos when I can't open the GUI, what file?

---

### Post by claracc on 2013-07-06
> **axept said:**
> And where should I disable third party repos when I can't open the GUI, what file?

You can do it in file /etc/apt/sources.list

You edit this file as root: ```
gksudo gedit /etc/apt/sources.list
```
and write a # sign before the line referring to the ppa you want to disable

---

### Post by axept on 2013-07-06
There's no third party PPA's in there, like steampowered, private launchpad etc..

---

### Post by axept on 2013-07-09
Up you go..

No one that have a clue why I can't add PPA's or even  start Update Manager? When System shows there's updates for my system I  can't install them, because the install button doesn't work..

---

### Post by Bashing-om on 2013-07-09
axept; Hi !

Sources may be located in
/etc/apt/sources.list
or
the directory /etc/apt/sources.list.d/
```
ls -la /etc/apt/sources.list.d/
```
more likely the PPAs' source is in that directory.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by axept on 2013-07-10
Thanks, 

Tried many things last night with live help. Seemed to be a corrupt *pyc file somewhere. Whatever I did, I got the same error. So this morning I gave up and installed a fresh install of 13.04..

---

