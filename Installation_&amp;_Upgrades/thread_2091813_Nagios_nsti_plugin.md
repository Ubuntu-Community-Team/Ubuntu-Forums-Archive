---
title: "Nagios nsti plugin"
date: 2012-12-06
forum: Installation &amp; Upgrades
---

### Post by MocroNL on 2012-12-06
Hey guys I have followed this tutorial:
[http://linuxdrops.com/step-by-step-installation-guide-for-nsti/](http://linuxdrops.com/step-by-step-installation-guide-for-nsti/)

I have nagios up and running using Ubuntu 11.10.

I have done everything what the tutorial told me to do but I cannot open [localhost]/nsti/. When starting ./install.py I get some errors mabye those are related to my problem?


Successfully added permissions to database.
Successfully tested connection with new authentication.
Sucessfully edited snmptt.ini.
**cp: cannot create regular file `/etc/httpd/conf.d/': No such file or directory**
Sucessfully moved apache configuration.
Traceback (most recent call last):
  File "./install.py", line 384, in <module>
    main()
  File "./install.py", line 374, in main
    edit_nsti_conf()
  File "./install.py", line 283, in edit_nsti_conf
    for line in inplacefile:
  File "/usr/lib/python2.7/fileinput.py", line 253, in next
    line = self.readline()
  File "/usr/lib/python2.7/fileinput.py", line 322, in readline
    os.rename(self._filename, self._backupfilename)
OSError: [Errno 2] No such file or directory

Thanks in advance!

---

