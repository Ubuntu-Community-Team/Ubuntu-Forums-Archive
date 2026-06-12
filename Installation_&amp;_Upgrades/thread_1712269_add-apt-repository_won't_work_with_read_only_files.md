---
title: "add-apt-repository won't work with read only files"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by zyberwoof on 2011-03-22
I have a **sources.list** file that is shared by many machines.  For this reason, **/etc/apt/sources.list** is a symbolic link for me.  Most of the machines do not have the ability to edit that file.

When I try to add an additional PPA to a machine with add-apt-repository, I get a "permission denied" error because of this file.  I have tried moving the file to **/etc/apt/sources.list.d/sources.list** and even renaming it to **/etc/apt/sources.list.d/lucid.list**.  Regaurdless of how I do it, it works fine with apt-get, but not with add-apt-repository.  

Here is some example output:
```
zyberwoof@duo:/etc/apt/sources.list.d$ sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 42, in <module>
    if not sp.add_source_from_line(line):
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 636, in add_source_from_line
    self.set_modified_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 425, in set_modified_sourceslist
    self.save_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 589, in save_sourceslist
    self.sourceslist.save()
  File "/usr/lib/python2.6/dist-packages/aptsources/sourceslist.py", line 367, in save
    files[source.file] = open(source.file, "w")
IOError: [Errno 13] Permission denied: '/etc/apt/sources.list.d/lucid.list'
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv B34505EA326FEAEA07E3618DEF4186FE247510BE
gpg: requesting key 247510BE from hkp server keyserver.ubuntu.com
gpg: key 247510BE: "Launchpad PPA for Ubuntu Mozilla Daily Build Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```

Is there some way for me to have this type of setup and use add-apt-repository?

---

