---
title: "Can't upgrade or install software: of broken package openstack-dashboard-ubunt-theme"
date: 2015-07-21
forum: Installation &amp; Upgrades
---

### Post by carolsand on 2015-07-21
I had Openstack installed and removed it using synaptic. All associated packages seem to uninstall except for openstack-dashboard-ubuntu-theme. Now this package is said to be broken according to dpkg and apt.
All of my attempts to uninstall and/ or fix this broken package have failed.

I receive errors when attempting any of the following commands: 
```

sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 openstack-dashboard-ubuntu-theme : Depends: openstack-dashboard (= 1:2015.1~rc1-0ubuntu2) but 1:2015.1.0-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.

sudo apt-get autoremove && sudo apt-get autoclean openstack-dashboard-ubuntu-theme
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 openstack-dashboard-ubuntu-theme : Depends: openstack-dashboard (= 1:2015.1~rc1-0ubuntu2) but 1:2015.1.0-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.
sudo dpkg --remove --force-remove-reinstreq openstack-dashboard-ubuntu-theme
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
(Reading database ... 1012855 files and directories currently installed.)
Removing openstack-dashboard-ubuntu-theme (1:2015.1~rc1-0ubuntu2) ...
Collecting and compressing static assets...
Warning: Could not import Horizon dependencies. This is normal during installation.
Traceback (most recent call last):
  File "manage.py", line 25, in <module>
    execute_from_command_line(sys.argv)
  File "/usr/lib/python2.7/dist-packages/django/core/management/__init__.py", line 385, in execute_from_command_line
    utility.execute()
  File "/usr/lib/python2.7/dist-packages/django/core/management/__init__.py", line 345, in execute
    settings.INSTALLED_APPS
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 46, in __getattr__
    self._setup(name)
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 42, in _setup
    self._wrapped = Settings(settings_module)
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 94, in __init__
    mod = importlib.import_module(self.SETTINGS_MODULE)
  File "/usr/lib/python2.7/importlib/__init__.py", line 37, in import_module
    __import__(name)
  File "/usr/share/openstack-dashboard/openstack_dashboard/settings.py", line 28, in <module>
    from openstack_dashboard.static_settings import get_staticfiles_dirs  # noqa
  File "/usr/share/openstack-dashboard/openstack_dashboard/static_settings.py", line 20, in <module>
    import horizon.xstatic.main
  File "/opt/stack/horizon/horizon/__init__.py", line 55, in <module>
    assert Dashboard
NameError: name 'Dashboard' is not defined
dpkg: error processing package openstack-dashboard-ubuntu-theme (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 openstack-dashboard-ubuntu-theme

sudo apt-get --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.16.0-36-generic linux-image-extra-3.16.0-36-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openstack-dashboard-ubuntu-theme
The following packages will be upgraded:
  openstack-dashboard-ubuntu-theme
1 upgraded, 0 newly installed, 0 to remove and 257 not upgraded.
2 not fully installed or removed.
Need to get 0 B/71.0 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 1012856 files and directories currently installed.)
Preparing to unpack .../openstack-dashboard-ubuntu-theme_1%3a2015.1.0-0ubuntu1_all.deb ...
Unpacking openstack-dashboard-ubuntu-theme (1:2015.1.0-0ubuntu1) over (1:2015.1~rc1-0ubuntu2) ...
Collecting and compressing static assets...
Warning: Could not import Horizon dependencies. This is normal during installation.
Traceback (most recent call last):
  File "manage.py", line 25, in <module>
    execute_from_command_line(sys.argv)
  File "/usr/lib/python2.7/dist-packages/django/core/management/__init__.py", line 385, in execute_from_command_line
    utility.execute()
  File "/usr/lib/python2.7/dist-packages/django/core/management/__init__.py", line 345, in execute
    settings.INSTALLED_APPS
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 46, in __getattr__
    self._setup(name)
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 42, in _setup
    self._wrapped = Settings(settings_module)
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 94, in __init__
    mod = importlib.import_module(self.SETTINGS_MODULE)
  File "/usr/lib/python2.7/importlib/__init__.py", line 37, in import_module
    __import__(name)
  File "/usr/share/openstack-dashboard/openstack_dashboard/settings.py", line 28, in <module>
    from openstack_dashboard.static_settings import get_staticfiles_dirs  # noqa
  File "/usr/share/openstack-dashboard/openstack_dashboard/static_settings.py", line 20, in <module>
    import horizon.xstatic.main
  File "/opt/stack/horizon/horizon/__init__.py", line 55, in <module>
    assert Dashboard
NameError: name 'Dashboard' is not defined
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Collecting and compressing static assets...
Warning: Could not import Horizon dependencies. This is normal during installation.
Traceback (most recent call last):
  File "manage.py", line 25, in <module>
    execute_from_command_line(sys.argv)
  File "/usr/lib/python2.7/dist-packages/django/core/management/__init__.py", line 385, in execute_from_command_line
    utility.execute()
  File "/usr/lib/python2.7/dist-packages/django/core/management/__init__.py", line 345, in execute
    settings.INSTALLED_APPS
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 46, in __getattr__
    self._setup(name)
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 42, in _setup
    self._wrapped = Settings(settings_module)
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 94, in __init__
    mod = importlib.import_module(self.SETTINGS_MODULE)
  File "/usr/lib/python2.7/importlib/__init__.py", line 37, in import_module
    __import__(name)
  File "/usr/share/openstack-dashboard/openstack_dashboard/settings.py", line 28, in <module>
    from openstack_dashboard.static_settings import get_staticfiles_dirs  # noqa
  File "/usr/share/openstack-dashboard/openstack_dashboard/static_settings.py", line 20, in <module>
    import horizon.xstatic.main
  File "/opt/stack/horizon/horizon/__init__.py", line 55, in <module>
    assert Dashboard
NameError: name 'Dashboard' is not defined
dpkg: error processing archive /var/cache/apt/archives/openstack-dashboard-ubuntu-theme_1%3a2015.1.0-0ubuntu1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Collecting and compressing static assets...
Warning: Could not import Horizon dependencies. This is normal during installation.
Traceback (most recent call last):
  File "manage.py", line 25, in <module>
    execute_from_command_line(sys.argv)
  File "/usr/lib/python2.7/dist-packages/django/core/management/__init__.py", line 385, in execute_from_command_line
    utility.execute()
  File "/usr/lib/python2.7/dist-packages/django/core/management/__init__.py", line 345, in execute
    settings.INSTALLED_APPS
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 46, in __getattr__
    self._setup(name)
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 42, in _setup
    self._wrapped = Settings(settings_module)
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 94, in __init__
    mod = importlib.import_module(self.SETTINGS_MODULE)
  File "/usr/lib/python2.7/importlib/__init__.py", line 37, in import_module
    __import__(name)
  File "/usr/share/openstack-dashboard/openstack_dashboard/settings.py", line 28, in <module>
    from openstack_dashboard.static_settings import get_staticfiles_dirs  # noqa
  File "/usr/share/openstack-dashboard/openstack_dashboard/static_settings.py", line 20, in <module>
    import horizon.xstatic.main
  File "/opt/stack/horizon/horizon/__init__.py", line 55, in <module>
    assert Dashboard
NameError: name 'Dashboard' is not defined
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/openstack-dashboard-ubuntu-theme_1%3a2015.1.0-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Any suggestions?
Thanks in advance
;):mad:

---

### Post by bapoumba on 2015-07-22
[http://packages.ubuntu.com/vivid-updates/openstack-dashboard-ubuntu-theme](http://packages.ubuntu.com/vivid-updates/openstack-dashboard-ubuntu-theme)
You have the 1:2015.1.0-0ubuntu1: vivid-updates package installed. From the first error line, it requires 1:2015.1~rc1-0ubuntu2 which is the vivid version. That does not make much sense to me, other than you have fiddled with your source.list in the mean time, or not run an update.

So please post the outputs to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by carolsand on 2015-07-23
Thanks for your assistance.
Here's the output you requested:
```

cat -n /etc/apt/sources.list
     1	
     2	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     3	# newer versions of the distribution.
     4	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid main restricted
     5	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid main restricted
     6	
     7	## Major bug fix updates produced after the final release of the
     8	## distribution.
     9	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates main restricted
    10	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates main restricted
    11	
    12	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    13	## team. Also, please note that software in universe WILL NOT receive any
    14	## review or updates from the Ubuntu security team.
    15	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid universe
    16	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid universe
    17	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates universe
    18	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates universe
    19	
    20	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    21	## team, and may not be under a free licence. Please satisfy yourself as to 
    22	## your rights to use the software. Also, please note that software in 
    23	## multiverse WILL NOT receive any review or updates from the Ubuntu
    24	## security team.
    25	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid multiverse
    26	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid multiverse
    27	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates multiverse
    28	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates multiverse
    29	
    30	## N.B. software from this repository may not have been tested as
    31	## extensively as that contained in the main release, although it includes
    32	## newer versions of some applications which may provide useful features.
    33	## Also, please note that software in backports WILL NOT receive any review
    34	## or updates from the Ubuntu security team.
    35	
    36	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security main restricted
    37	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security main restricted
    38	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security universe
    39	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security universe
    40	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security multiverse
    41	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security multiverse
    42	
    43	## Uncomment the following two lines to add software from Canonical's
    44	## 'partner' repository.
    45	## This software is not part of Ubuntu, but is offered by Canonical and the
    46	## respective vendors as a service to Ubuntu users.
    47	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
    48	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
    49	
    50	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-proposed multiverse restricted universe main
    51	# deb [http://www.openprinting.org/download/printdriver/debian/](http://www.openprinting.org/download/printdriver/debian/) lsb3.1 gutenprint # disabled on upgrade to saucy

ls -la /etc/apt/sources.list.d
total 88
drwxr-xr-x 2 root root 4096 May 19 20:03 .
drwxr-xr-x 6 root root 4096 Jul 21 17:27 ..
-rw-r--r-- 1 root root  178 Jul 23 11:11 google-chrome.list
-rw-r--r-- 1 root root  210 Apr 27 15:38 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root  178 Jul 23 11:11 google-chrome.list.save
-rw-r--r-- 1 root root  182 Jul 23 11:11 google-talkplugin.list
-rw-r--r-- 1 root root  214 Apr 27 15:38 google-talkplugin.list.distUpgrade
-rw-r--r-- 1 root root  182 Jul 23 11:11 google-talkplugin.list.save
-rw-r--r-- 1 root root   66 Jul 23 11:11 medibuntu.list
-rw-r--r-- 1 root root  227 Apr 27 15:38 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root   66 Jul 23 11:11 medibuntu.list.save
-rw-r--r-- 1 root root  196 Jul 23 11:11 noobslab-icons-raring.list
-rw-r--r-- 1 root root  196 Apr 27 15:38 noobslab-icons-raring.list.distUpgrade
-rw-r--r-- 1 root root  196 Jul 23 11:11 noobslab-icons-raring.list.save
-rw-r--r-- 1 root root  300 Jul 23 11:11 noobslab-themes-raring.list
-rw-r--r-- 1 root root  300 Apr 27 15:38 noobslab-themes-raring.list.distUpgrade
-rw-r--r-- 1 root root  300 Jul 23 11:11 noobslab-themes-raring.list.save
-rw-r--r-- 1 root root  134 Jul 23 11:11 noobslab-ubuntu-themes-vivid.list
-rw-r--r-- 1 root root  132 Jul 23 11:11 noobslab-ubuntu-themes-vivid.list.save
-rw-r--r-- 1 root root  470 Jul 23 11:11 salience-team-salience-devel-ppa-raring.list
-rw-r--r-- 1 root root  470 Apr 27 15:38 salience-team-salience-devel-ppa-raring.list.distUpgrade
-rw-r--r-- 1 root root  470 Jul 23 11:11 salience-team-salience-devel-ppa-raring.list.save

tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main # disabled on upgrade to utopic

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

==> /etc/apt/sources.list.d/google-talkplugin.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

==> /etc/apt/sources.list.d/google-talkplugin.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main # disabled on upgrade to utopic

==> /etc/apt/sources.list.d/google-talkplugin.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

==> /etc/apt/sources.list.d/medibuntu.list <==
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)

==> /etc/apt/sources.list.d/medibuntu.list.distUpgrade <==
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) trusty free non-free #Medibuntu - Ubuntu 13.04 "raring ringtail" disabled on upgrade to saucy disabled on upgrade to trusty

==> /etc/apt/sources.list.d/medibuntu.list.save <==
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)

==> /etc/apt/sources.list.d/noobslab-icons-raring.list <==
# deb [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) saucy main # disabled on upgrade to saucy
# deb-src [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) raring main # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/noobslab-icons-raring.list.distUpgrade <==
# deb [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) saucy main # disabled on upgrade to saucy
# deb-src [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) raring main # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/noobslab-icons-raring.list.save <==
# deb [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) saucy main # disabled on upgrade to saucy
# deb-src [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) raring main # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/noobslab-themes-raring.list <==
# deb [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) saucy main # disabled on upgrade to saucy
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) raring main # disabled on upgrade to trusty
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) raring main # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/noobslab-themes-raring.list.distUpgrade <==
# deb [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) saucy main # disabled on upgrade to saucy
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) raring main # disabled on upgrade to trusty
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) raring main # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/noobslab-themes-raring.list.save <==
# deb [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) saucy main # disabled on upgrade to saucy
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) raring main # disabled on upgrade to trusty
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) raring main # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/noobslab-ubuntu-themes-vivid.list <==
# deb [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) vivid main
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) vivid main

==> /etc/apt/sources.list.d/noobslab-ubuntu-themes-vivid.list.save <==
# deb [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) vivid main
deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) vivid main

==> /etc/apt/sources.list.d/salience-team-salience-devel-ppa-raring.list <==
# deb [http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu](http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu) saucy main # disabled on upgrade to saucy
# deb-src [http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu](http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu) raring main # disabled on upgrade to trusty
# deb-src [http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu](http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu) raring main # disabled on upgrade to trusty
# deb-src [http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu](http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu) raring main # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/salience-team-salience-devel-ppa-raring.list.distUpgrade <==
# deb [http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu](http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu) saucy main # disabled on upgrade to saucy
# deb-src [http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu](http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu) raring main # disabled on upgrade to trusty
# deb-src [http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu](http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu) raring main # disabled on upgrade to trusty
# deb-src [http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu](http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu) raring main # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/salience-team-salience-devel-ppa-raring.list.save <==
# deb [http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu](http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu) saucy main # disabled on upgrade to saucy
# deb-src [http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu](http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu) raring main # disabled on upgrade to trusty
# deb-src [http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu](http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu) raring main # disabled on upgrade to trusty
# deb-src [http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu](http://ppa.launchpad.net/salience-team/salience-devel-ppa/ubuntu) raring main # disabled on upgrade to trusty

sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid InRelease                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates InRelease                      
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security Release.gpg [933 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed InRelease
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security Release [63.5 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) vivid InRelease                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid Release.gpg                             
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates Release.gpg [933 B]
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid Release.gpg                                        
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed Release.gpg [933 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid Release                                            
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid Release                                              
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main Sources [28.1 kB]                      
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates Release [63.5 kB]                          
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted Sources [28 B]      
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid/partner Sources                                               
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe Sources [13.2 kB]                   
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse Sources [1,957 B]                         
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid/partner amd64 Packages                               
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed Release [217 kB]                  
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main amd64 Packages [85.8 kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid/partner i386 Packages                               
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted amd64 Packages [28 B]                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/main Sources                                           
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe amd64 Packages [41.7 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/restricted Sources                                                        
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse amd64 Packages [3,494 B]     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/universe Sources                                                          
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main i386 Packages [85.2 kB]       
Ign [http://archive.canonical.com](http://archive.canonical.com) vivid/partner Translation-en                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/multiverse Sources                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/main amd64 Packages                                
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted i386 Packages [28 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/restricted amd64 Packages                          
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe i386 Packages [41.7 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/universe amd64 Packages                            
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse i386 Packages [3,675 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/multiverse amd64 Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main Translation-en 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/universe i386 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/universe Translation-en
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/main Sources [64.6 kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/restricted Sources [28 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/universe Sources [27.6 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/multiverse Sources [1,957 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/main amd64 Packages [152 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/restricted amd64 Packages [28 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/universe amd64 Packages [84.0 kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/multiverse amd64 Packages [3,494 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/main i386 Packages [151 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/restricted i386 Packages [28 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/universe i386 Packages [84.0 kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/multiverse i386 Packages [3,675 B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/main Translation-en [74.7 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/restricted Translation-en
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/universe Translation-en [47.9 kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/multiverse amd64 Packages [551 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/restricted amd64 Packages [3,278 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/universe amd64 Packages [21.3 kB]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/main amd64 Packages [86.5 kB]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/multiverse i386 Packages [551 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/restricted i386 Packages [3,271 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/universe i386 Packages [23.1 kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/main i386 Packages [85.1 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/restricted Translation-en
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/universe Translation-en [17.6 kB]
Fetched 1,588 kB in 5s (273 kB/s)           
Reading package lists... Done

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 openstack-dashboard-ubuntu-theme : Depends: openstack-dashboard (= 1:2015.1~rc1-0ubuntu2) but 1:2015.1.0-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by PaulW2U on 2015-07-23
Please use code tags for terminal output as they improve readability.

If you are using New Reply button - highlight text and use the # button in the text box header. If you are using Quick Reply then add [noparse]```
 at the beginning of the section and 
```[/noparse] at the end.

---

### Post by bapoumba on 2015-07-24
The only ppa that is active is this one :
```
==> /etc/apt/sources.list.d/noobslab-ubuntu-themes-vivid.list.save <==
# deb http://ppa.launchpad.net/noobslab/themes/ubuntu vivid main
deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu vivid main
```

As the package you have trouble with is :
```
The following packages have unmet dependencies:
 openstack-dashboard-ubuntu-theme : Depends: openstack-dashboard (= 1:2015.1~rc1-0ubuntu2) but 1:2015.1.0-0ubuntu1 is installed
```
And the ppa is for themes, please try disabling the noobslab ppa, then update/upgrade again.

---

### Post by carolsand on 2015-08-27
```

casubuntu-lt:~$ cat /etc/apt/sources.list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner

``````

casubuntu-lt:~$ sudo apt-get update
[sudo] password for carolsand: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) vivid InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security Release.gpg [933 B]
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid Release.gpg                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed InRelease
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security Release [63.5 kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid Release.gpg                              
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates Release.gpg [933 B]            
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid/partner Sources                                    
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed Release.gpg [933 B]                        
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid/partner amd64 Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid Release                                       
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main Sources [38.8 kB]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid/partner i386 Packages                   
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates Release [63.5 kB]                            
Hit [http://archive.canonical.com](http://archive.canonical.com) vivid/partner Translation-en                                        
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted Sources [28 B]      
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe Sources [15.9 kB]     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse Sources [1,966 B]   
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed Release [217 kB]   
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main amd64 Packages [108 kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted amd64 Packages [28 B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe amd64 Packages [51.9 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/main Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/restricted Sources     
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse amd64 Packages [3,496 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/universe Sources                               
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main i386 Packages [107 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/multiverse Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/main amd64 Packages                            
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted i386 Packages [28 B]      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/restricted amd64 Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/universe amd64 Packages
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe i386 Packages [51.9 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/multiverse amd64 Packages                          
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse i386 Packages [3,680 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/main i386 Packages                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/restricted i386 Packages   
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/main Translation-en [56.8 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/multiverse Translation-en                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/universe i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/main Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/restricted Translation-en
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) vivid-security/universe Translation-en [32.4 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid/universe Translation-en                       
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/main Sources [78.5 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/restricted Sources [1,366 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/universe Sources [35.8 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/multiverse Sources [1,966 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/main amd64 Packages [185 kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/restricted amd64 Packages [3,283 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/universe amd64 Packages [99.9 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/multiverse amd64 Packages [3,496 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/main i386 Packages [184 kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/restricted i386 Packages [3,273 B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/universe i386 Packages [99.8 kB]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/multiverse i386 Packages [3,680 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/main Translation-en [89.7 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/multiverse Translation-en                                                                                                                                                                  
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/restricted Translation-en [569 B]                                                                                                                                                       
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-updates/universe Translation-en [58.0 kB]                                                                                                                                                       
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/multiverse amd64 Packages [551 B]                                                                                                                                                      
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/restricted amd64 Packages [28 B]                                                                                                                                                       
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/universe amd64 Packages [18.4 kB]                                                                                                                                                      
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/main amd64 Packages [73.1 kB]                                                                                                                                                          
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/multiverse i386 Packages [551 B]                                                                                                                                                       
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/restricted i386 Packages [28 B]                                                                                                                                                        
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/universe i386 Packages [20.2 kB]                                                                                                                                                       
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/main i386 Packages [72.4 kB]                                                                                                                                                           
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/main Translation-en [27.1 kB]                                                                                                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/multiverse Translation-en                                                                                                                                                                 
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/restricted Translation-en [28 B]                                                                                                                                                       
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) vivid-proposed/universe Translation-en [15.6 kB]                                                                                                                                                      
Fetched 1,895 kB in 7s (245 kB/s)                                                                                                                                                                                                         
Reading package lists... Done

``````

:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 openstack-dashboard-ubuntu-theme : Depends: openstack-dashboard (= 1:2015.1~rc1-0ubuntu2) but 1:2015.1.1-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.

``````

casubuntu-lt:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openstack-dashboard-ubuntu-theme
The following packages will be upgraded:
  openstack-dashboard-ubuntu-theme
1 upgraded, 0 newly installed, 0 to remove and 332 not upgraded.
3 not fully installed or removed.
Need to get 0 B/70.9 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 1007809 files and directories currently installed.)
Preparing to unpack .../openstack-dashboard-ubuntu-theme_1%3a2015.1.1-0ubuntu1_all.deb ...
Unpacking openstack-dashboard-ubuntu-theme (1:2015.1.1-0ubuntu1) over (1:2015.1~rc1-0ubuntu2) ...
Collecting and compressing static assets...
Warning: Could not import Horizon dependencies. This is normal during installation.
Traceback (most recent call last):
  File "manage.py", line 25, in <module>
    execute_from_command_line(sys.argv)
  File "/usr/lib/python2.7/dist-packages/django/core/management/__init__.py", line 385, in execute_from_command_line
    utility.execute()
  File "/usr/lib/python2.7/dist-packages/django/core/management/__init__.py", line 345, in execute
    settings.INSTALLED_APPS
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 46, in __getattr__
    self._setup(name)
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 42, in _setup
    self._wrapped = Settings(settings_module)
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 94, in __init__
    mod = importlib.import_module(self.SETTINGS_MODULE)
  File "/usr/lib/python2.7/importlib/__init__.py", line 37, in import_module
    __import__(name)
  File "/usr/share/openstack-dashboard/openstack_dashboard/settings.py", line 28, in <module>
    from openstack_dashboard.static_settings import get_staticfiles_dirs  # noqa
  File "/usr/share/openstack-dashboard/openstack_dashboard/static_settings.py", line 20, in <module>
    import horizon.xstatic.main
  File "/opt/stack/horizon/horizon/__init__.py", line 55, in <module>
    assert Dashboard
NameError: name 'Dashboard' is not defined
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Collecting and compressing static assets...
Warning: Could not import Horizon dependencies. This is normal during installation.
Traceback (most recent call last):
  File "manage.py", line 25, in <module>
    execute_from_command_line(sys.argv)
  File "/usr/lib/python2.7/dist-packages/django/core/management/__init__.py", line 385, in execute_from_command_line
    utility.execute()
  File "/usr/lib/python2.7/dist-packages/django/core/management/__init__.py", line 345, in execute
    settings.INSTALLED_APPS
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 46, in __getattr__
    self._setup(name)
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 42, in _setup
    self._wrapped = Settings(settings_module)
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 94, in __init__
    mod = importlib.import_module(self.SETTINGS_MODULE)
  File "/usr/lib/python2.7/importlib/__init__.py", line 37, in import_module
    __import__(name)
  File "/usr/share/openstack-dashboard/openstack_dashboard/settings.py", line 28, in <module>
    from openstack_dashboard.static_settings import get_staticfiles_dirs  # noqa
  File "/usr/share/openstack-dashboard/openstack_dashboard/static_settings.py", line 20, in <module>
    import horizon.xstatic.main
  File "/opt/stack/horizon/horizon/__init__.py", line 55, in <module>
    assert Dashboard
NameError: name 'Dashboard' is not defined
dpkg: error processing archive /var/cache/apt/archives/openstack-dashboard-ubuntu-theme_1%3a2015.1.1-0ubuntu1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
Collecting and compressing static assets...
Warning: Could not import Horizon dependencies. This is normal during installation.
Traceback (most recent call last):
  File "manage.py", line 25, in <module>
    execute_from_command_line(sys.argv)
  File "/usr/lib/python2.7/dist-packages/django/core/management/__init__.py", line 385, in execute_from_command_line
    utility.execute()
  File "/usr/lib/python2.7/dist-packages/django/core/management/__init__.py", line 345, in execute
    settings.INSTALLED_APPS
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 46, in __getattr__
    self._setup(name)
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 42, in _setup
    self._wrapped = Settings(settings_module)
  File "/usr/lib/python2.7/dist-packages/django/conf/__init__.py", line 94, in __init__
    mod = importlib.import_module(self.SETTINGS_MODULE)
  File "/usr/lib/python2.7/importlib/__init__.py", line 37, in import_module
    __import__(name)
  File "/usr/share/openstack-dashboard/openstack_dashboard/settings.py", line 28, in <module>
    from openstack_dashboard.static_settings import get_staticfiles_dirs  # noqa
  File "/usr/share/openstack-dashboard/openstack_dashboard/static_settings.py", line 20, in <module>
    import horizon.xstatic.main
  File "/opt/stack/horizon/horizon/__init__.py", line 55, in <module>
    assert Dashboard
NameError: name 'Dashboard' is not defined
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/openstack-dashboard-ubuntu-theme_1%3a2015.1.1-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by carolsand on 2015-08-27
How can I completely remove Horizon (Openstack)? 
I think this is my problem.

---

