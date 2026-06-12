---
title: "I broke my apt.  How do I fix?"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by mickfromperth on 2007-05-22
Hi. 

I'm a realtive gumbie when it comes to these types of things.  A while ago I tried to install vdr and freevo.  I got those two apps working but I'm not sure how.  Now it's time to upgrade these things and I guess that means I need to address what I broke all those months ago.

When I aptupgrade anything, I get the following..
---
mick@freevo:/etc/vdr/plugins$ sudo aptitude purge
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been automatically kept back:
  fuse-utils libfuse2 libmysqlclient15off libntfs-3g0 mysql-client-5.0 mysql-common mysql-server-5.0 python-imaging
The following packages have been kept back:
  automatix2 brasero cdparanoia democracyplayer democracyplayer-data desktop-file-utils evolution-data-server
  evolution-data-server-common firefox firefox-gnome-support language-pack-en language-pack-gnome-en libcamel1.2-8
  libcdparanoia0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-7
  libedataserverui1.2-8 libegroupwise1.2-12 libexchange-storage1.2-2 libgphoto2-2 libgphoto2-port0 liblircclient-dev
  liblircclient0 libnautilus-extension1 lirc lirc-modules-source mysql-server nautilus nautilus-data ntfs-3g
  popularity-contest rdesktop synaptic tzdata ubuntu-docs unrar update-manager update-notifier vim-common vim-tiny
  wine
0 packages upgraded, 0 newly installed, 0 to remove and 52 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up python-freevo (1.6.2-0edgy2) ...
Can't list /usr/share/python-support/python-freevo/freevo
Can't list /usr/share/python-support/python-freevo/freevo
usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/python-freevo does not exist
dpkg: error processing python-freevo (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python-freevo
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
mick@freevo:/etc/vdr/plugins$

---

In that list I can see 2 issues.  One, freevo-python; and Two, perl.

In the case of freevo, I think I deleted the files that apt installed.  Ever since then I cannot apt-get remove.  or I can, but it has affect on the listing in apt...

---
mick@freevo:/etc/vdr/plugins$ sudo aptitude remove -f python-freevo
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been automatically kept back:
  fuse-utils libfuse2 libmysqlclient15off libntfs-3g0 mysql-client-5.0 mysql-common mysql-server-5.0 python-imaging
The following packages have been kept back:
  automatix2 brasero cdparanoia democracyplayer democracyplayer-data desktop-file-utils evolution-data-server
  evolution-data-server-common firefox firefox-gnome-support language-pack-en language-pack-gnome-en libcamel1.2-8
  libcdparanoia0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-7
  libedataserverui1.2-8 libegroupwise1.2-12 libexchange-storage1.2-2 libgphoto2-2 libgphoto2-port0 liblircclient-dev
  liblircclient0 libnautilus-extension1 lirc lirc-modules-source mysql-server nautilus nautilus-data ntfs-3g
  popularity-contest rdesktop synaptic tzdata ubuntu-docs unrar update-manager update-notifier vim-common vim-tiny
  wine
The following packages will be REMOVED:
  python-freevo
0 packages upgraded, 0 newly installed, 1 to remove and 52 not upgraded.
Need to get 0B of archives. After unpacking 2605kB will be freed.
Writing extended state information... Done
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 158700 files and directories currently installed.)
Removing python-freevo ...
usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/python-freevo does not exist
dpkg: error processing python-freevo (--remove):
 subprocess pre-removal script returned error exit status 2
postinst called with unknown argument `abort-remove'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-freevo
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
mick@freevo:/etc/vdr/plugins$
---

And then there is Perl and the locale errors.  I'm not sure what I did there.  I also don't want to remove it.  How do I fix it?

Assistance appreciate.

Mike

---

