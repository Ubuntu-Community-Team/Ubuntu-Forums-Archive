---
title: "Broken packages -&gt; broken system"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by AllesMeins on 2007-01-08
Hi,

i've the following problem. I tried to remove the package "doodle" when something went wrong. Unfortunaly i can't remember the error message. No i ended up with Synaptic always complaining about 2 broken packages, when trying to remove any package it lists a long list of packages that have to be removed with it (including gnome, kde, mozilla, openoffice...)

When starting the "Software Update Manager" it sugests running "sudo apt-get install -f". This fails with the following messages:

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  doodled portmap
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gamin libgamin0
The following packages will be REMOVED:
  doodled
The following NEW packages will be installed:
  gamin libgamin0
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/116kB of archives.
After unpacking 221kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 134014 files and directories currently installed.)
Removing doodled ...
Stopping doodle daemon: invoke-rc.d: initscript doodled, action "stop" failed.
dpkg: error processing doodled (--remove):
 subprocess pre-removal script returned error exit status 1
Starting doodle daemon: /usr/bin/doodled: error while loading shared libraries: libfam.so.0: cannot open shared object file: No such file or directory
invoke-rc.d: initscript doodled, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 doodled
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm not sure if it has anything at all to do with this problem, but scince then i can't use gnome anymore: After logging in it keeps sending bugreport after bugreport and there isn't anything i can do about it because the "send bugreport"-window keeps popping up.

I hope you can help me - i didn't thought i could mess up my system so seriously without even touching some system-internals.

I'm using amd64-Edgy Ubuntu

---

### Post by ajgreeny on 2007-01-08
In synaptic have you tried using *Edit>Fix Broken Packages*?

For all I know it may do the same as *sudo apt-get install -f*, but I do remember using synaptic to do this a couple of versions of ubuntu ago, and it worked like a dream, so perhaps worth a try.

---

### Post by tokj on 2007-01-08
Try to remove *doodled* with the command:

```
sudo dpkg --remove --force-all doodled
```

---

### Post by AllesMeins on 2007-01-08
> **ajgreeny said:**
> In synaptic have you tried using *Edit>Fix Broken Packages*?

I get an message:
*E: doodled: subprocess pre-removal script returned error exit status 1*

When looking under "Details":
```
Preconfiguring packages ...
(Reading database ... 134001 files and directories currently installed.)
Removing doodled ...
Stopping doodle daemon: invoke-rc.d: initscript doodled, action "stop" failed.
dpkg: error processing doodled (--remove):
 subprocess pre-removal script returned error exit status 1
Starting doodle daemon: /usr/bin/doodled: error while loading shared libraries: libfam.so.0: cannot open shared object file: No such file or directory
invoke-rc.d: initscript doodled, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 doodled
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

[QUOTE=tokj]Try to remove doodled with the command:
sudo dpkg --remove --force-all doodled
[/QUOTE]

This fails as well. pretty much the same messages as before:

```
$ sudo dpkg --remove --force-all doodled
Password:
(Reading database ... 134001 files and directories currently installed.)
Removing doodled ...
Stopping doodle daemon: invoke-rc.d: initscript doodled, action "stop" failed.
dpkg: error processing doodled (--remove):
 subprocess pre-removal script returned error exit status 1
Starting doodle daemon: /usr/bin/doodled: error while loading shared libraries: libfam.so.0: cannot open shared object file: No such file or directory
invoke-rc.d: initscript doodled, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 doodled

```

---

### Post by tokj on 2007-01-08
In your directories exists a file named *libfam.so.0*?

---

### Post by AllesMeins on 2007-01-08
> **tokj said:**
> In your directories exists a file named *libfam.so.0*?

No, I guess it was already removed by apt-get in earlier tries to get rid of doodled. But why is a lib needed to remove a package?
And why tries apt-get to stop "doodled"? As far as i know it isn't even running (which indeed explains why it can't be stopped :) ).

---

### Post by AllesMeins on 2007-01-08
For the record:
I managed to fix it myself by changing *invoke-rc.d doodled stop || exit $?* to */bin/true || exit $?* in *var/lib/dpkg/info/doodled.prerm* and removing some of the leftover files manualy.

---

### Post by JRaz on 2007-01-22
Not the same program, but a similar problem nevertheless. Basically when I try to remove the package irmp3 I get the following error.

```
sudo dpkg --remove --force-all irmp3  
Password:
(Reading database ... 40475 files and directories currently installed.)
Removing irmp3 ...
Stopping irmp3: invoke-rc.d: initscript irmp3, action "stop" failed.
dpkg: error processing irmp3 (--remove):
 subprocess pre-removal script returned error exit status 1
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Starting irmp3: irmp3.
Errors were encountered while processing:
 irmp3
```

Any help would be appreciated.

---

