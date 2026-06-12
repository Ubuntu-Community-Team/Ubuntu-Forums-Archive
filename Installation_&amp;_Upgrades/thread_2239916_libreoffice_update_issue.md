---
title: "libreoffice update issue"
date: 2014-08-16
forum: Installation &amp; Upgrades
---

### Post by maclenin on 2014-08-16
This is exactly what my terminal is telling me (as I try to complete an upgrade to the latest version of libreoffice in xubuntu 12.04):

```

:~$ sudo aptitude safe-upgrade
The following packages will be upgraded: 
  libreoffice-base 
The following partially installed packages will be configured:
  libreoffice libreoffice-report-builder-bin 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,138 kB of archives. After unpacking 2,614 kB will be used.
Do you want to continue? [Y/n/?] Y
dpkg: dependency problems prevent configuration of libreoffice-base:
 libreoffice-base depends on libreoffice-base-core (= 1:4.3.0-0ubuntu1~precise1); however:
  Version of libreoffice-base-core on system is 1:4.3.0-3ubuntu1~precise1.
 libreoffice-base depends on libreoffice-base-drivers (= 1:4.3.0-0ubuntu1~precise1); however:
  Version of libreoffice-base-drivers on system is 1:4.3.0-3ubuntu1~precise1.
 libreoffice-base depends on libreoffice-core (= 1:4.3.0-0ubuntu1~precise1); however:
  Version of libreoffice-core on system is 1:4.3.0-3ubuntu1~precise1.
 libreoffice-core (1:4.3.0-3ubuntu1~precise1) breaks libreoffice-base (<< 1:4.3.0-3ubuntu1~precise1) and is installed.
  Version of libreoffice-base to be configured is 1:4.3.0-0ubuntu1~precise1.
dpkg: error processing libreoffice-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of libreoffice-report-builder-bin:
 libreoffice-report-builder-bin depends on libreoffice-base; however:
  Package libreoffice-base is not configured yet.
dpkg: error processing libreoffice-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice:
 libreoffice depends on libreoffice-base; however:
  Package libreoffice-base is not configured yet.
 libreoffice depends on libreoffice-report-builder-bin; however:
  Package libreoffice-report-builder-bin is not configured yet.No apport report written because MaxReports has already been reached

dpkg: error processing libreoffice (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 libreoffice-base
 libreoffice-report-builder-bin
 libreoffice
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libreoffice-base:
 libreoffice-base depends on libreoffice-base-core (= 1:4.3.0-0ubuntu1~precise1); however:
  Version of libreoffice-base-core on system is 1:4.3.0-3ubuntu1~precise1.
 libreoffice-base depends on libreoffice-base-drivers (= 1:4.3.0-0ubuntu1~precise1); however:
  Version of libreoffice-base-drivers on system is 1:4.3.0-3ubuntu1~precise1.
 libreoffice-base depends on libreoffice-core (= 1:4.3.0-0ubuntu1~precise1); however:
  Version of libreoffice-core on system is 1:4.3.0-3ubuntu1~precise1.
 libreoffice-core (1:4.3.0-3ubuntu1~precise1) breaks libreoffice-base (<< 1:4.3.0-3ubuntu1~precise1) and is installed.
  Version of libreoffice-base to be configured is 1:4.3.0-0ubuntu1~precise1.
dpkg: error processing libreoffice-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-report-builder-bin:
 libreoffice-report-builder-bin depends on libreoffice-base; however:
  Package libreoffice-base is not configured yet.
dpkg: error processing libreoffice-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice:
 libreoffice depends on libreoffice-base; however:
  Package libreoffice-base is not configured yet.
 libreoffice depends on libreoffice-report-builder-bin; however:
  Package libreoffice-report-builder-bin is not configured yet.
dpkg: error processing libreoffice (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libreoffice-base
 libreoffice-report-builder-bin
 libreoffice
                                         
:~$ 
```

A similar issue is described here: [http://askubuntu.com/questions/512162/libreoffice-base-not-configured-yet#new-answer](http://askubuntu.com/questions/512162/libreoffice-base-not-configured-yet#new-answer)

Current libreoffice version "installed and working" on my xubutnu 12.04 desktop: 4.3.0.4

Thanks for any guidance.

---

### Post by nadrach on 2014-08-16
Two bugs.

I am on Lubuntu 14.04 64 bit.

(1) Upgrade to LO 4.3.0.3 from 4.3.0.x fails because two packages in 4.3.0.3 are referencing the same file and the second cannot overwrite the file whilst the first package also owns it.

(2) Removal of previous libreoffice base package fails because of a missing line in a post.rm file, resulting in an unexpected "fi". The final line of the second command in the file is missing. There are two multi-line commands in this file, one for removal and one for aborted upgrade (there may also be an extra auto-added one-line command line at the bottom). The structure is the same for both commands, just options different. I assumed that the last line of the second command was likely the same as for the first, edited the file with "vi", reran the removal via apt-get and it succeeded.

I have now removed of the rest LO via Synaptic, but I suspect that reinstalling LO will call 4.3.0.3, and the package dual ownership of a file will reappear. I'll report back shortly.

---

### Post by nadrach on 2014-08-16
OK, re-install of LO 4.3.0.3 after removal is OK.

Damaged file in LO 4.3.0.x libreoffice-base was **/var/lib/dpkg/info/libreoffice-base.postrm** which should have read as follows, but the line in **bold** was missing:

> #!/bin/sh

set -e


if [ "$1" = remove -o "$1" = abort-install -o "$1" = disappear ]; then
	dpkg-divert --package $DPKG_MAINTSCRIPT_PACKAGE --remove --rename \
		--divert /usr/lib/libreoffice/share/basic/dialog.xlc.noaccess \
                        /usr/lib/libreoffice/share/basic/dialog.xlc
	dpkg-divert --package $DPKG_MAINTSCRIPT_PACKAGE --remove --rename \
		--divert /usr/lib/libreoffice/share/basic/script.xlc.noaccess \
                        /usr/lib/libreoffice/share/basic/script.xlc
fi
if [ "$1" = abort-upgrade ] && dpkg --compare-versions "$2" lt dpkg --compare-versions "$2" lt 1:4.3.0~beta1-1; then
	dpkg-divert --package $DPKG_MAINTSCRIPT_PACKAGE --remove --rename \
		--divert /usr/lib/libreoffice/share/basic/dialog.xlc.noaccess \
                        /usr/lib/libreoffice/share/basic/dialog.xlc
	dpkg-divert --package $DPKG_MAINTSCRIPT_PACKAGE --remove --rename \
		--divert /usr/lib/libreoffice/share/basic/script.xlc.noaccess \
			**/usr/lib/libreoffice/share/basic/script.xlc**
fi

# Automatically added by dh_installmenu
if [ -x "`which update-menus 2>/dev/null`" ]; then update-menus ; fi
# End automatically added section


exit 0


---

### Post by nadrach on 2014-08-16
OK, slight nomenclature error:
LO = 4.3.0.4
Ubuntu packages = 1:4.3.0-3ubuntu1~trusty1

---

### Post by ajgreeny on 2014-08-16
> **nadrach said:**
> OK, re-install of LO 4.3.0.3 after removal is OK.

Damaged file in LO 4.3.0.x libreoffice-base was **/var/lib/dpkg/info/libreoffice-base.postrm** which should have read as follows, but the line in **bold** was missing:
**WOW!**
Thanks for that info.

I edited the file that you mention and added the missing line then removed just the libreoffice-base package, which worked this time, and then reinstalled it, which also worked perfectly.

No more broken package!

Thank you so much.

---

### Post by maclenin on 2014-08-16
Indeed! **WOW!** +1! 

Thanks, **nadrach**, for the solution!

As **ajgreeny** (and per your suggestion), I edited the **/var/lib/dpkg/info/libreoffice-base.postrm** file, removed **libreoffice-base**, using aptitude and then reinstalled **libreoffice**, using:

```
sudo aptitude install libreoffice-base
sudo aptitude install libreoffice
```

All seems repaired!

Thanks, again, **nadrach!**

NB: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1354557](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1354557)

---

### Post by nadrach on 2014-08-17
No problem. You're welcome.

---

### Post by maclenin on 2014-08-18
**nadrach!** Behold, the [fruits of your labours]("http://askubuntu.com/questions/512162/libreoffice-base-not-configured-yet#new-answer")....

---

### Post by Ricardo_Augusto on 2014-08-20
Thanks, nadrach! =d>

---

