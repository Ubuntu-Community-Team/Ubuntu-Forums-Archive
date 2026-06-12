---
title: "Feisty Issues"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Rootcomputing on 2007-04-22
I will cut right to the chase...


I go to install, ran into a few initial issues, but nothing major...now for some reason apache has lost its mind..I have attemped removing apache2 myself, but have had no luck. I can't even restart it. To my knowledge I have the only apache I have running is on my server not this machine. Anyone have any Ideas...Thanks. 


ERROR:

After unpacking 418MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: apache2-common: dependency problems, but removing anyway as you request:
 apache2-mpm-worker depends on apache2-common (= 2.0.55-4ubuntu4).
(Reading database ... 123381 files and directories currently installed.)
Removing apache2-common ...
 * Stopping apache 2.0 web server...                                     [fail] 
invoke-rc.d: initscript apache2, action "stop" failed.
dpkg: error processing apache2-common (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 apache2-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by BoneKracker on 2007-04-22
That's nuts.  It would appear that it is trying to install apache.

I would remove it, then use the synaptic gui to try and figure out what I had installed that the package management system might think has apache2 as a dependency.

---

