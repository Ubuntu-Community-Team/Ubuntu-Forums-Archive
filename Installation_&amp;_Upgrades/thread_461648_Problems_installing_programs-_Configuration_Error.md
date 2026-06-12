---
title: "Problems installing programs- Configuration Error"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by gdoermann on 2007-06-01
Whenever I install or uninstall programs it gives me the following error:

An Error Occurred
E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured



(Reading database ... 149011 files and directories currently installed.)
Removing acidrip ...
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d : initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured

Can ANYONE help?  The programs install, but they don't always work correctly.

This was a log from the uninstall, but I get the same errors when installing.

---

### Post by rillip on 2007-06-01
I have NO idea.  It looks like you installed a redhat package/rpm that isn't able to resolve it's dependancies.  RPM's are notorious for being a pain in the butt like this.  Ubuntu doesn't use them by default, and I don't know what the cluster suite is or how you installed it; I doubt from the repositories.  You'll probably have to find out from the package maker what it requires and install all the dependancies by hand.

---

### Post by gdoermann on 2007-06-01
I get the error installing from the Add/Remove Programs menu.  I type in the root password and it installs the program, giving the first error box.  i click close and it pops up another window saying it was installed with errors.  I click the details button and it gives the the terminal log.  I have also tried using the ```
"sudo aptitude update && sudo aptitude upgrade
```
If a program that gave me this error when I originally installed it, the update gives the same error.

I just reinstalled acidrip (to get the error) from the terminal and this is what happened:

```

doermann@doermann-desktop:~$ sudo apt-get install acidrip
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  acidrip
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/55.4kB of archives.
After unpacking 295kB of additional disk space will be used.
Selecting previously deselected package acidrip.
(Reading database ... 148997 files and directories currently installed.)
Unpacking acidrip (from .../acidrip_0.14-0.2ubuntu4_all.deb) ...
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Setting up acidrip (0.14-0.2ubuntu4) ...

Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

SOMEBODY please let me know what I can do.

---

### Post by gdoermann on 2007-06-02
ok... I found the solution.  It is a bug in clvm, a cluster management program.  (See [this page]("http://packages.ubuntu.com/feisty/admin/clvm") for more info on clvm)

So you need to remove clvm and the reinstall it.  The problem is the bug keeps you from uninstalling or reinstalling clvm.  So follow the instructions on this thread to uninstall it:

[http://ubuntuforums.org/showpost.php?p=2522803&postcount=14]("http://ubuntuforums.org/showpost.php?p=2522803&postcount=14")

Then run this code in the terminal:

```
sudo apt-get install clvm
```

Volia!  Your bug is fixed!

---

