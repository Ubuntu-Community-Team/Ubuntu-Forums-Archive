---
title: "My packages are broken and I can't fix them."
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by DanielLC on 2012-11-13
I installed an old version of python and I think some i386 files when I was trying to install some legacy software. I have since given up and I'm trying to get Ubuntu to work the way it did before.

In particular, I can't seem to get back to the current version of python. Everything I do seems to just give me a list of unmet dependencies that need the current version of python, including "sudo apt-get -f" and even "sudo apt-get upgrade python".

The only thing I can think of that I haven't tried is uninstalling python, which will uninstall 252 packages. I don't know what most of them are, but it seems to include all the games I've downoaded, which I'd rather keep.

---

### Post by ibjsb4 on 2012-11-13
Lets see what you got to work with.  Please post the output of apt-get update.  And what are you running? 12.04/12.10; 32/64bit

---

### Post by DanielLC on 2012-11-13
I'm using 64 bit. I don't know how to check the version number.

Here's what I got from sudo apt-get -f install:

```
daniellc@Machina-Ex-Deo:~/Desktop$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libplot2c2 libpano13-bin hugin-data libpano13-2 libimage-exiftool-perl
  libzthread-2.3-2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python
Suggested packages:
  python-doc
The following packages will be upgraded:
  python
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
23 not fully installed or removed.
Need to get 0 B/166 kB of archives.
After this operation, 96.3 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: warning: there's no installed package matching python:amd64
dpkg: dependency problems prevent configuration of apparmor:
 apparmor depends on python; however:
  Package python is not configured yet.
dpkg: error processing apparmor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on python; however:
  Package python is not configured yet.
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    dpkg: error processing update-notifier-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-release:
 lsb-release depends on python (>= 2.7.1-0ubuntu2); however:
  Version of python on system is 2.6.6-2ubuntu1.
 lsb-release depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing lsb-release (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apparmor-utils:
 apparmor-utils depends on apparmor (>= 2.6.1-4ubuntu1); however:
  Package apparmor is not configured yet.
 apparmor-utils depends on python (>= 2.7.1-0ubuntu2); however:
  Version of python on system is 2.6.6-2ubuntu1.
 apparmor-utils depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing apparmor-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-problemNo apport report written because the error message indicates its a followup error from a previous failure.
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                                                       No apport report written because MaxReports is reached already
                                     No apport report written because MaxReports is reached already
                   -report:
 python-problem-report depends on python (>= 2.7.1-0ubuntu2); however:
  Version of python on system is 2.6.6-2ubuntu1.
 python-problem-report depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-problem-report (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python (>= 2.7.1-0ubuntu2); however:
  Version of python on system is 2.6.6-2ubuntu1.
 python-apport depends on python (<< 2.8); however:
  Package python is not configured yet.
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.
 python-apport depends on lsb-release; however:
  Package lsb-release is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python (>= 2No apport report written because MaxReports is reached already
             No apport report written because MaxReports is reached already
                                                                           No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already
                                       No apport report written because MaxReports is reached already
                     No apport report written because MaxReports is reached already
   No apport report written because MaxReports is reached already
                                                                 No apport report written because MaxReports is reached already
                                               .6); however:
  Package python is not configured yet.
 apport depends on python-apport (>= 2.0.1-0ubuntu14); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python (>= 2.4); however:
  Package python is not configured yet.
 apport-gtk depends on python-apport (>= 2.0.1-0ubuntu14); however:
  Package python-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on lsb-release; however:
  Package lsb-release is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-branNo apport report written because MaxReports is reached already
                                             No apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already
         No apport report written because MaxReports is reached already
                                                                       No apport report written because MaxReports is reached already
                                                     No apport report written because MaxReports is reached already
                                   No apport report written because MaxReports is reached already
                 ding:
 firefox-branding depends on firefox (>= 9.0); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-globalmenu:
 firefox-globalmenu depends on firefox (= 16.0.2+build1-0ubuntu0.12.04.1); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-globalmenu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox; however:
  Package firefox is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-common:
 jockey-common depends on python (>= 2.7.1-0ubuntu2); however:
  Version of python on system is 2.6.6-2ubuntu1.
 jockey-common depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing jockey-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on python; however:
  Package python is not configured yet.
 jockey-gtk depends on jockey-common (= 0.9.7-0ubuntu7.4); however:
  Package jockey-common is not configured yet.
dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of onboard:
 onboard depends on python (>= 2.7.1-0ubuntu2); however:
  Version of python on system is 2.6.6-2ubuntu1.
 onboard depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing onboard (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-notifier-common (= 0.119ubuntu8.6); however:
  Package update-notifier-common is not configured yet.
 update-notifier depends on python; however:
  Package python is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon:
 python-aptdaemon depends on python (>= 2.7.1-0ubuntu2); however:
  Version of python on system is 2.6.6-2ubuntu1.
 python-aptdaemon depends on python (<< 2.8); however:
  Package python is not configured yet.
dpkg: error processing python-aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aptdaemon:
 aptdaemon depends on python; however:
  Package python is not configured yet.
 aptdaemon depends on python-aptdaemon (= 0.43+bzr805-0ubuntu6); however:
  Package python-aptdaemon is not configured yet.
dpkg: error processing aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon.gtkwidgets:
 python-aptdaemon.gtkwidgets depends on python (>= 2.7.1-0ubuntu2); however:
  Version of python on system is 2.6.6-2ubuntu1.
 python-aptdaemon.gtkwidgets depends on python (<< 2.8); however:
  Package python is not configured yet.
 python-aptdaemon.gtkwidgets depends on python-aptdaemon (= 0.43+bzr805-0ubuntu6); however:
  Package python-aptdaemon is not configured yet.
dpkg: error processing python-aptdaemon.gtkwidgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon.gtk3widgets:
 python-aptdaemon.gtk3widgets depends on python (>= 2.7.1-0ubuntu2); however:
  Version of python on system is 2.6.6-2ubuntu1.
 python-aptdaemon.gtk3widgets depends on python (<< 2.8); however:
  Package python is not configured yet.
 python-aptdaemon.gtk3widgets depends on python-aptdaemon (= 0.43+bzr805-0ubuntu6); however:
  Package python-aptdaemon is not configured yet.
dpkg: error processing python-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-aptdaemon-gtk:
 python-aptdaemon-gtk depends on python-aptdaemon.gtkwidgets (= 0.43+bzr805-0ubuntu6); however:
  Package python-aptdaemon.gtkwidgets is not configured yet.
 python-aptdaemon-gtk depends on python-aptdaemon.gtk3widgets (= 0.43+bzr805-0ubuntu6); however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing python-aptdaemon-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sessioninstaller:
 sessioninstaller depends on python (>= 2.7.1-0ubuntu2); however:
  Version of python on system is 2.6.6-2ubuntu1.
 sessioninstaller depends on python (<< 2.8); however:
  Package python is not configured yet.
 sessioninstaller depends on aptdaemon (>= 0.30); however:
  Package aptdaemon is not configured yet.
 sessioninstaller depends on python-aptdaemon.gtk3widgets; however:
  Package python-aptdaemon.gtk3widgets is not configured yet.
dpkg: error processing sessioninstaller (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apparmor
 update-notifier-common
 lsb-release
 apparmor-utils
 python-problem-report
 python-apport
 apport
 apport-gtk
 firefox
 firefox-branding
 firefox-globalmenu
 firefox-gnome-support
 jockey-common
 jockey-gtk
 onboard
 update-notifier
 python-aptdaemon
 aptdaemon
 python-aptdaemon.gtkwidgets
 python-aptdaemon.gtk3widgets
 python-aptdaemon-gtk
 sessioninstaller
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ibjsb4 on 2012-11-13
And have you tried to update just to see if it will update python to 2.7 ?

sudo apt-get update

If it will, then follow with:

sudo apt-get upgrade

---

### Post by DanielLC on 2012-11-14
Didn't work.

---

### Post by NikTh on 2012-11-14
Hmmm , when breakage of python is here , re-installation is near. 

If you have a liveCD-USB , boot from there and try to re-install without remove your personal data. (of course you will lose all your programs .. etc)
The other way is to backup your data (to a safe place) and install from scratch.
If you choose the re-install,
you have to interfere with advanced installation - partitioning . "Something Else" except if Ubuntu gives you the option to Re-install the version without remove your personal data /home. 
You will see that at the installer window (with the options). 

If you choose to continue with the "Something Else" option , you have to leave the "Format" box Un-ticked  and select the correct partition (where Ubuntu=> /root is installed) to re-install.

See some pictures 
[http://ubuntuforums.org/attachment.php?attachmentid=225347&d=1349852728](http://ubuntuforums.org/attachment.php?attachmentid=225347&d=1349852728)
[http://ubuntuforums.org/attachment.php?attachmentid=225348&d=1349852728](http://ubuntuforums.org/attachment.php?attachmentid=225348&d=1349852728)

Sorry but this is my best advice. It will be more "painless" than to struggle to resolve the problem.

Thanks

---

### Post by ibjsb4 on 2012-11-14
A reinstall should also update a package

sudo apt-get --reinstall install python

If you get a reply of python is not installed

sudo apt-get install python

And NikTH probably has the answer, didn't know you was a poet  :)

---

### Post by NikTh on 2012-11-14
> **ibjsb4 said:**
> 
And NikTH probably has the answer, didn't know you was a poet  :)
Neither do I . :P

Faced such problems in past and realize are very difficult to resolve them (for me), but are good problems if you want to learn things. Keep struggle and you never know :)

I'll keep in touch with this Thread.

---

### Post by SlugSlug on 2012-11-14
will aptitude help?

```
sudo apt-get install aptitude
```

```
sudo aptitude reinstall python
```

---

### Post by DanielLC on 2012-11-15
Python won't reinstall or install.

Aptitude won't install.

---

### Post by NikTh on 2012-11-15
Give the results 
```
apt-cache policy python2.7
python -V
```

Thanks

---

