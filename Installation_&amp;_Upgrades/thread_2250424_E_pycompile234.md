---
title: "E: pycompile:234"
date: 2014-10-28
forum: Installation &amp; Upgrades
---

### Post by fflorent on 2014-10-28
Hello everyone!

I try to install packages with apt-get, but this morning , I do not understand what is wrong.
Would it be possible to help me understand the error apt-get me back please ?

Thank you very much,
Florent .

Here is the return in question :
```
[B]

florent-R530-R730-R540 florent # apt-get install python[/B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
15 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up update-manager-core (1:0.156.14.17) ...
[B]E: pycompile:234: Requested versions are not installed
dpkg: error processing update-manager-core (--configure):
 subprocess installed post-installation script returned error exit status 3[/B]
[B]dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on update-manager-core (>= 1:0.156.14.15); however:
  Package update-manager-core is not configured yet.
dpkg: error processing update-notifier-common (--configure):
 dependency problems - leaving unconfigured[/B]
Setting up python-uno (1:3.5.7-0ubuntu6.1) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                              E: pycompile:234: Requested versions  are not installed
[B]dpkg: error processing python-uno (--configure):
 subprocess installed post-installation script returned error exit status 3[/B]
dpkg: dependency problems prevent configuration of libreoffice-emailmerge:
 libreoffice-emailmerge depends on python-uno | python3-uno; however:
  Package python-uno is not configured yet.
  Package python3-uno is not installed.
dpkg: error processing libreoffice-emailmerge (--configure):
 dependency problems - leaving unconfigured
Setting up python-bottle (0.10.6-1) ...
No apport report written because MaxReports has already been reached
                                                                    E: pycompile:234: Requested versions are not installed
dpkg: error processing python-bottle (--configure):
 subprocess installed post-installation script returned error exit status 3
No apport report written because MaxReports has already been reached
                                                                    Setting up python-bson (2.1-1ubuntu0.1) ...
[B]E: pycompile:234: Requested versions are not installed
dpkg: error processing python-bson (--configure):
 subprocess installed post-installation script returned error exit status 3[/B]
No apport report written because MaxReports has already been reached
                                                                    Setting up python-jinja2 (2.6-1ubuntu0.1) ...
E: pycompile:234: Requested versions are not installed
dpkg: error processing python-jinja2 (--configure):
 subprocess installed post-installation script returned error exit status 3
Setting up python-libvirt (0.9.8-2ubuntu17.20) ...
No apport report written because MaxReports has already been reached
                                                                    E: pycompile:234: Requested versions are not installed
dpkg: error processing python-libvirt (--configure):
 subprocess installed post-installation script returned error exit status 3
No apport report written because MaxReports has already been reached
                                                                    Setting up python-libxml2 (2.7.8.dfsg-5.1ubuntu4.11) ...
E: pycompile:234: Requested versions are not installed
dpkg: error processing python-libxml2 (--configure):
 subprocess installed post-installation script returned error exit status 3
No apport report written because MaxReports has already been reached
                                                                    Setting up python-problem-report (2.0.1-0ubuntu17.7) ...
E: pycompile:234: Requested versions are not installed
dpkg: error processing python-problem-report (--configure):
 subprocess installed post-installation script returned error exit status 3
No apport report written because MaxReports has already been reached
                                                                     dpkg:  dependency problems prevent configuration of python-pymongo:
 python-pymongo depends on python-bson (= 2.1-1ubuntu0.1); however:
  Package python-bson is not configured yet.
dpkg: error processing python-pymongo (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Setting up python-sqlalchemy (0.7.4-1ubuntu0.1) ...
E: pycompile:234: Requested versions are not installed
dpkg: error processing python-sqlalchemy (--configure):
 subprocess installed post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of python-sqlalchemy-ext:
 python-sqlalchemy-ext depends on python-sqlalchemy (= 0.7.4-1ubuntu0.1); however:
  Package python-sqlalchemy is not configured yet.
dpkg: error processing python-sqlalchemy-ext (--configure):
 dependency problems - leaving unconfigured
Setting up python-magic (5.09-2ubuntu0.5) ...
No apport report written because MaxReports has already been reached
                                                                     No  apport report written because MaxReports has already been reached
                                                                                                                                          E:  pycompile:234: Requested versions are not installed
dpkg: error processing python-magic (--configure):
 subprocess installed post-installation script returned error exit status 3
No apport report written because MaxReports has already been reached
                                                                    Setting up python-pefile (1.2.9.1-1) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2372, in <module>
    main()
  File "/usr/bin/pycentral", line 2366, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1505, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
     raise ValueError, "/usr/bin/python does not match the python default  version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.7
dpkg: error processing python-pefile (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Processing triggers for libreoffice-common ...
Errors were encountered while processing:
 update-manager-core
 update-notifier-common
 python-uno
 libreoffice-emailmerge
 python-bottle
 python-bson
 python-jinja2
 python-libvirt
 python-libxml2
 python-problem-report
 python-pymongo
 python-sqlalchemy
 python-sqlalchemy-ext
 python-magic
 python-pefile
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by bapoumba on 2014-10-28
You seem to be running on precise. How did this happen ? Do you have all the standard repos enabled in your sources.list ?
What does **sudo apt-get -f install **return ?

---

### Post by fflorent on 2014-10-28
Hi !

Unfortunately, I can't give you the result of this command, because I have partially purged python... and now I have no more desktop !
And I can't re-install mate desktop... because I have the same errors than above.

OOoohh, bad day, guys...

---

### Post by bapoumba on 2014-10-28
Oh.. That is why you were trying to reinstall python then.. Is dpkg working ? You could wget the files and install them with dpkg. You'd have to do the same for the dependencies.
[http://packages.ubuntu.com/precise/python-minimal](http://packages.ubuntu.com/precise/python-minimal) > [http://archive.ubuntu.com/ubuntu/pool/main/p/python2.7/python2.7_2.7.3.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/p/python2.7/python2.7_2.7.3.orig.tar.gz)
[http://packages.ubuntu.com/precise/python2.7](http://packages.ubuntu.com/precise/python2.7) > [http://archive.ubuntu.com/ubuntu/pool/main/p/python2.7/python2.7_2.7.3.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/p/python2.7/python2.7_2.7.3.orig.tar.gz)

I would backup all the important files you cannot afford to loose, if not done already. I have never encountered such a situation. Maybe some others have ?

---

### Post by ian-weisser on 2014-10-28
apt-get won't work until the dependency mess is cleared up.
It will continue to give you the same error over and over.

So you have a couple choices to make progress:
1) Use dpkg instead to install packages, working the dependency order manually instead of using apt.
2) Uninstall update-manager (and everything else that depends upon the purged Python packages)
3) Backup and reinstall

Which direction do you want to try first?

---

### Post by fflorent on 2014-11-01
Thank you for your answer.

Finally, I completely reinstall my Linux distribution, and I installed Ubuntu instead of Mint.

Thank you for your help,

florent

---

