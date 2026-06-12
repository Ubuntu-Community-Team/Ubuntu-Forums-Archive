---
title: "can't install google chrome browser on 11.04"
date: 2011-09-30
forum: Installation &amp; Upgrades
---

### Post by dancingLoki on 2011-09-30
Tried to install google chrome browser on 11.04 because I'm told it is faster & may work better with flash video.

Problem is it gives errors on install:
> Unpacking google-chrome-stable (from google-chrome-stable_current_i386.deb) ...
dpkg: dependency problems prevent configuration of google-chrome-stable:
 google-chrome-stable depends on libcurl3; however:
  Package libcurl3 is not installed.
dpkg: error processing google-chrome-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Errors were encountered while processing:
 google-chrome-stable

So a little research & I find this: [http://techthatclicks.com/2011/07/18/how-to-install-google-chrome-on-ubuntu-11-04/](http://techthatclicks.com/2011/07/18/how-to-install-google-chrome-on-ubuntu-11-04/)

so I try: > sudo aptitude install google-chrome-stable

result:
> The following NEW packages will be installed:
  libcurl3{a} 
The following partially installed packages will be configured:
  google-chrome-stable 
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 220 kB of archives. After unpacking 553 kB will be used.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.
E: I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

This still doesn't seem good.

I got this too somehow in a popup:
> Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?

I figure why not?  So I hit the Repir button.  Here is the result:

> There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Details:

> Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

Am I doing something wrong?  So far Ubuntu Linux has been a real pain.

---

### Post by dancingLoki on 2011-09-30
OK, following code worked:

> sudo apt-get -f install

which takes awhile & required accepting one of those legalese agreements.

then

> sudo apt-get install google-chrome-stable

and it works!!!

---

