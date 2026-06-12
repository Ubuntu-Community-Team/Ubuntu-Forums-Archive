---
title: "Weird error when trying to sudo-apt get packages"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by danran on 2006-10-12
Hi, i'm trying to download the packages with the command: "sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 cgwd cgwd-themes" but it's returning this:

>>>>>
dan@CatEgg:~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 cgwd cgwd-themes
Reading package lists... Done
Building dependency tree... Done
libgl1-mesa is already the newest version.
xserver-xorg is already the newest version.
Note, selecting emerald instead of cgwd
Package cgwd-themes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  emerald-themes
E: Package cgwd-themes has no installation candidate
dan@CatEgg:~$
<<<<<

What does that mean??

I'm using Dapper 6.06 XUbuntu.  I have all the repositories added through the Synaptic configuration and I ran "sudo apt-get update" and "sudo apt-get upgrade"!  :confused: 

Thanks in advance!

--Dan W.

---

### Post by adwait on 2006-10-12
It means that cgwd-themes package has been replaced by emerald-themes which is a similar package, so instead of trying to install cgwd-themes try installing emerald-themes.

---

### Post by danran on 2006-10-12
Hi, well I substituted emerald and i'm getting a different error now:

>>>>>
dan@CatEgg:~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg l ibglitz-glx1 cgwd emerald-themes
Password:
Reading package lists... Done
Building dependency tree... Done
libgl1-mesa is already the newest version.
xserver-xorg is already the newest version.
Note, selecting emerald instead of cgwd
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-plugins (>= 0.2) but it is not going to be installed
  emerald: Depends: libwnck18 but it is not going to be installed
  xserver-xgl: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
E: Broken packages
dan@CatEgg:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
dan@CatEgg:~$ sudo apt-get install libwnck18
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libwnck18: Depends: libatk1.0-0 (>= 1.12.1) but 1.11.4-0ubuntu1 is to be insta lled
             Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
             Depends: libcairo2 (>= 1.2.4) but 1.0.4-0ubuntu1 is to be installed
             Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be inst alled
             Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1 is to be insta lled
             Depends: libpango1.0-0 (>= 1.14.5) but 1.12.3-0ubuntu3 is to be ins talled
E: Broken packages
<<<<<

It looks like i'm missing a bunch of basic libraries and stuff here.  I have build-essentials installed.  libc6 is also installed.  Is there anything else?  I dont get it...  :confused:

---

