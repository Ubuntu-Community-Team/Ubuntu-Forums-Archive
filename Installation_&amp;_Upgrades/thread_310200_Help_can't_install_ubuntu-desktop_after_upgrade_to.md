---
title: "Help can't install ubuntu-desktop after upgrade to edgy"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by doctorjay420 on 2006-11-30
I upgraded to Egdy from Dapper using the upgrade option in the software update section.  The installation seemed to go fine until it tried to install ubuntu-desktop, and then it crashed, and I have not been able to get it working since.  This is what happens when i try to install the package:

janstey@momndad:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gnome-app-install
The following NEW packages will be installed:
  gnome-app-install ubuntu-desktop
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 195kB of archives.
After unpacking, 1081kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy/main gnome-app-install 0.2.21 [178kB]
Get:2 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) edgy/main ubuntu-desktop 1.30 [17.0kB]
Fetched 195kB in 5s (33.6kB/s)            
Selecting previously deselected package gnome-app-install.
(Reading database ... 178674 files and directories currently installed.)
Unpacking gnome-app-install (from .../gnome-app-install_0.2.21_all.deb) ...
Selecting previously deselected package ubuntu-desktop.
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.30_i386.deb) ...
Setting up gnome-app-install (0.2.21) ...
Traceback (most recent call last):
  File "/usr/sbin/update-app-install", line 12, in ?
    import xdg.DesktopEntry
ImportError: No module named xdg.DesktopEntry
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-app-install
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have looked everywhere for an aswer, please help...

Jay

---

### Post by styracosaurus on 2006-11-30
You could try aptitude. Someone told me that it has better dependency resolution, and that seems to be the problem.

You can use it the same way you use apt-get, on the command line and everything, and it supports the same commands, "install" "update" etc

But I am in no way sure.

---

### Post by doctorjay420 on 2006-12-01
I tried that too, it still doesn't work.  What does this affect? it's seems that ubuntu-desktop would be an important package?

---

### Post by styracosaurus on 2006-12-01
So you tried to upgrade to Edgy and during the upgrade it crashed while install ubuntu-desktop? And then when you tried to install it later it still crashes?

"ubuntu-desktop" is a metapackage that has as dependencies all the other packages that make up the desktop environment. I am not sure, but I assume that would mean GNOME and all the stuff that comes with, since "kubuntu-desktop" will install KDE and "xubuntu-desktop" will install xfce. I THINK that the docs say that this is equivalent to installing Kubuntu or Xubuntu from scratch using a CD, but I have found this to be otherwise. Maybe I did something wrong though.

I think there is a sticky somewhere that has information about upgrading... I actually upgraded from Ubuntu Dapper to Kubuntu Edgy using a CD, just reinstalled the whole thing, but I had some other issues (like wanting to dump Windows) I know you can do it without reinstalled with a CD... but I think there are some issues. Also Edgy is really new, so there might be some wrinkles.

---

### Post by towsonu2003 on 2006-12-01
ubuntu-desktop is a meta package that depends on gnome-app-install, which you cannot install. I don't know why this is happening: 
> import xdg.DesktopEntry
ImportError: No module named xdg.DesktopEntry

Did you install anything before that wasn't part of ubuntu repositories? adding new weird repositories and so on maybe?

try installing these two:
```

sudo apt-get python2.4 python-xdg
```
and then try installing ubuntu-desktop again.[1] 

also I searched around the forums (for keyword "xdg.DesktopEntry") and there are a number of unresolved threads out there, so file a bug report at this address: [https://bugs.launchpad.net/distros/ubuntu/+source/update-manager/+bugs](https://bugs.launchpad.net/distros/ubuntu/+source/update-manager/+bugs)

this will tell the developers that something is wrong, and you might get a clue on what to do to fix the issue from them :) 

PS. bug reports are not for getting support.

[1] Reference for this: [http://www.realistanew.com/2005/03/18/gnome-menu-editor/](http://www.realistanew.com/2005/03/18/gnome-menu-editor/) see comments 38 & 39

---

### Post by doctorjay420 on 2006-12-01
these packages are already installed:

python2.4 python-xdg

I guess i'll have to see what come from the bug report.

Thank You.

---

### Post by doctorjay420 on 2006-12-01
Update ..

I installed the pyxdg package, and now i get a different error:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Setting up gnome-app-install (0.2.21) ...
Traceback (most recent call last):
  File "/usr/sbin/update-app-install", line 13, in ?
    import gdbm
ImportError: No module named gdbm
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-app-install
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@momndad:/home/janstey# apt-get install python-gdbm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-gdbm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Setting up gnome-app-install (0.2.21) ...
Traceback (most recent call last):
  File "/usr/sbin/update-app-install", line 13, in ?
    import gdbm
ImportError: No module named gdbm
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-app-install; however:
  Package gnome-app-install is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-app-install
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)


now it can't find gdbm

---

### Post by Vevmesteren on 2007-01-28
same, or somewhat anyways, problem here. I dist-upgraded, now I have a constant icon in my notification area telling me that I have a software upgrade pending, when I try, I am told that I need  a Distribution Upgrade. I try that and get the ubuntu-desktop installation error and the upgrade cannot proceed. I tried apt-get install ubuntu-desktop and get the following error:

```
sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: xorg but it is not going to be installed
E: Broken packages
```

---

### Post by fearpi on 2007-04-02
I have the same problem with not being able to find the gdbm module. Does anyone have any ideas?

Edit: I have been working on this problem for several hours now, and I have made some progress: It seems that the environment variable PYTHONPATH is nonexistent on my system. Setting it to a colon-delimited list of paths where my modules are (e.g. /usr/lib/python2.4/lib-dynload) seems to be helping. Will continue to work on the issue.

---

