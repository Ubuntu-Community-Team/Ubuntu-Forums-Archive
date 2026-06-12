---
title: "Python-numpy problem"
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Natalia- on 2010-03-06
Hey

Here is my problem. I upgraded from 9.10 to 10.04. I remember getting an error but I ignored it - then reboot my computer, everything was working perfectly, so I did not worry.

But now everytime I try to run update, or try to install a new software I can't, because there seems to be a problem with the package python-numpy. 

This is the error I get:

E: /var/cache/apt/archives/python-numpy_1%3a1.3.0-3build1_i386.deb: subprocess new pre-removal script returned error exit status 1

The following extra packages will be installed:
  python-numpy
Suggested packages:
  python-numpy-dbg python-nose
The following packages will be upgraded:
  python-numpy
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1,244kB of archives.
After this operation, 1,720kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 259493 files and directories currently installed.)
Preparing to replace python-numpy 1:1.3.0-3 (using .../python-numpy_1%3a1.3.0-3build1_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2195, in <module>
    main()
  File "/usr/bin/pycentral", line 2189, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1644, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 380, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 413, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error processing /var/cache/apt/archives/python-numpy_1%3a1.3.0-3build1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/python-numpy_1%3a1.3.0-3build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Then, I figured I could try to reinstall python-numpy. So I typed sudo apt-get install --reinstall python-numpy, but I get the following error:

nat@nat-laptop:~$ sudo apt-get install --reinstall python-numpy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 libqt4-assistant libgda-4.0-common nvidia-settings
  nvidia-185-libvdpau gtk-sharp2-gapi nvidia-185-kernel-source lsb-graphics
  python-twisted-runner lsb-desktop ncurses-term python-gda python-gdl
  python2.5 libboost-thread1.38.0 libtorrent-rasterbar5 python-twisted-mail
  libqt4-gui libgda-4.0-4 python-eggtrayicon python-twisted-lore
  python-twisted-conch python-twisted-news python-twisted-words libjline-java
  lsb pax python-twisted libffado1 libxml++2.6-2 lsb-printing rhino libdb4.6
  python-gksu2 libqt3-mt libboost-filesystem1.38.0 lsb-core
  libboost-system1.38.0 python-libtorrent libgdl-1-3 libgdl-1-common
  libboost-python1.38.0 lsb-cxx
Use 'apt-get autoremove' to remove them.
Suggested packages:
  python-numpy-dbg python-nose
The following packages will be upgraded:
  python-numpy
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1,244kB of archives.
After this operation, 1,720kB disk space will be freed.
(Reading database ... 259493 files and directories currently installed.)
Preparing to replace python-numpy 1:1.3.0-3 (using .../python-numpy_1%3a1.3.0-3build1_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2195, in <module>
    main()
  File "/usr/bin/pycentral", line 2189, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1644, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 380, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 413, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error processing /var/cache/apt/archives/python-numpy_1%3a1.3.0-3build1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/python-numpy_1%3a1.3.0-3build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


What should I do? 
Thank you for your help.

---

### Post by virtualnite on 2010-04-04
Natalia-

I am also experiencing the same (even though happened with the install of launchpad-integration) annoying and recurring (everytime i apt-get upgrade) pycentral error(s) in amd64 lucid and have filed a bug report that remains unanswered after two weeks... 

[https://bugs.launchpad.net/ubuntu/+source/python-central/+bug/540821](https://bugs.launchpad.net/ubuntu/+source/python-central/+bug/540821)

---

