---
title: "aborted intrepid-&gt;jaunty upgrade (python 2.6 issue)"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by ssfvt on 2009-12-29
Hi...I upgraded from Hardy to Intrepid without issues, then immediately followed with an attempt to further update with Jaunty. This failed with what looks like (at least on the surface) a Python issue. The updgrade aborted, and I'm in a weird state (both my system and me :-). I can't run update manager (complains about not finding /usr/bin/update-manager, though it is indeed there). I linked /usr/bin/python2.5  to /usr/bin/python just to see if I could get by, but no go. I have also played around marking python 2.6 for reinstall, also to no avail. 

I did find numerous references to a bug related to the python 2.6 install, as well as a reported patch (python-kinterbasdb.py26.patch), but that wasn't helpful (mostly due to my ingnorance). This seems to be related to my problem. So, I'm stuck. Here is the symptom below. Thanks in advance for any help!

The result of  sudo apt-get -f install 2>&1 | tee update.29Dec  is...

[FONT=Times New Roman]Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following extra packages will be installed:
  devhelp-common python-debian python2.6-minimal
The following NEW packages will be installed:
  python2.6-minimal
The following packages will be upgraded:
  devhelp-common python-debian
2 upgraded, 1 newly installed, 0 to remove and 298 not upgraded.
535 not fully installed or removed.
Need to get 0B/1418kB of archives.
After this operation, 4772kB of additional disk space will be used.
Do you want to continue [Y/n]? Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
Xlib:  extension "Generic Event Extension" missing on display ":0.0".
(Reading database ... 252113 files and directories currently installed.)
Unpacking python2.6-minimal (from .../python2.6-minimal_2.6.2-0ubuntu1_i386.deb) ...
new installation of python2.6-minimal; /usr/lib/python2.6/site-packages is a directory
which is expected a symlink to /usr/local/lib/python2.6/dist-packages.
please find the package shipping files in /usr/lib/python2.6/site-packages and
file a bug report to ship these in /usr/lib/python2.6/dist-packages instead
aborting installation of python2.6-minimal
dpkg: error processing /var/cache/apt/archives/python2.6-minimal_2.6.2-0ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python2.6-minimal_2.6.2-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]

---

### Post by ssfvt on 2009-12-29
OK, I looked a little deeper and discovered that the only contents of /usr/lib/python2.6/site-packages/ were put there by a custom "layer" that is supplied by my employer. I simply removed the directory and restarted the upgrade (sudo apt-get -f install) - it's proceeding as I write this. More later...

---

