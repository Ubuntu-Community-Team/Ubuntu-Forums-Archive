---
title: "update-manager crashed, 6.06 - 8.04"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by parsival on 2008-06-30
Hi Forum,

I was trying to use the update-manager to upgrade from 6.06 to 8.04 ie -- kdesu "update-manager -d"

I got a few error messages about various packages ie things like

The upgrade will continue but the 'python-vte' package may be in a not
working state. Please consider submitting a bugreport about
it.dependency problems - leaving unconfigured

and then

The upgrade aborts now. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).
Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
installArchives() failed


this ran for a while and then the update manager crashed!!!

The last error message on the screen (ie where the update manager was running) was

ImportError: /usr/local/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by
/usr/lib/libstdc++.so.6)
Could not import module, is a package upgrade in progress? Error:
/usr/local/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

Now X doesnt work and I have no network from that machine (yppasswd etc). I dont know why anything was looking for a library in /usr/local/lib and I suspect that this was the cause of the problem. I am now burning an "alternate CD" to see if I can revive the system

If I do get an alternate CD and try again -- what should I do to try and
salvage it?

Bye
parsival

---

### Post by Pumalite on 2008-06-30
Try at the Terminal, one at the time:
sudo dpkg --configure -a
sudo apt-get install -f 
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by parsival on 2008-07-05
Hi Pumalite,

with a lot of effort (and help),  it is now working!

1) dpkg --configure -a
bombed out with too many errors, so I started removing unconfigured packages one by one. Hours later, I gave up, as it didn't seem to be getting anywhere (I don't know, maybe it did some good).

2) I got the network card working and then

apt-get update -u
apt-get update  -f

but some packages were in such a bad state that they had to be installed before they could be removed. However, they could not be installed....

so I used the "dpkg --force-all" option a few times

3) it eventually worked!

I think the error message

/usr/local/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

showing /usr/local/libs being require by /usr/libs is the root cause of the problem. I am still getting this message. I am just unmounting
/usr/local (separate partition) when doing any upgrading etc.

Bye
parsival

---

### Post by Pumalite on 2008-07-05
I wish I had seen the output of :
sudo dpkg --configure -a

---

### Post by parsival on 2008-07-05
> **Pumalite said:**
> I wish I had seen the output of :
sudo dpkg --configure -a


Hi Pumalite,

I saved one ser of errors, but I dont remember if this was early in the process of removing packages or late. It is 292 lines
starting off with 

dpkg: dependency problems prevent configuration of libfontenc-dev:
 libfontenc-dev depends on libfontenc1 (= 1:1.0.4-2); however:
  Version of libfontenc1 on system is 1:1.0.1-0ubuntu2.
dpkg: error processing libfontenc-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libxfont-dev:
 libxfont-dev depends on libfontenc-dev (>= 1:1.0.1-1); however:
  Package libfontenc-dev is not configured yet.
dpkg: error processing libxfont-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xterm:
 xterm depends on xbitmaps; however:
  Package xbitmaps is not installed.
dpkg: error processing xterm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xfonts-base:
 xfonts-base depends on xfonts-utils (>= 1:1.0.0-6); however:
  Version of xfonts-utils on system is 6.8.2.1-5.
dpkg: error processing xfonts-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xfonts-100dpi:
 xfonts-100dpi depends on xfonts-utils (>= 1:1.0.0-6); however:
  Version of xfonts-utils on system is 6.8.2.1-5.
dpkg: error processing xfonts-100dpi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xlibs-static-dev:
 xlibs-static-dev depends on libfontenc-dev; however:
  Package libfontenc-dev is not configured yet.
 xlibs-static-dev depends on libxfont-dev; however:
  Package libxfont-dev is not configured yet.
dpkg: error processing xlibs-static-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xfonts-75dpi:
 xfonts-75dpi depends on xfonts-utils (>= 1:1.0.0-6); however:
  Version of xfonts-utils on system is 6.8.2.1-5.
dpkg: error processing xfonts-75dpi (--configure):
 dependency problems - leaving unconfigured
Setting up python-central (0.6.7ubuntu0.1) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1891, in <module>
    main()
  File "/usr/bin/pycentral", line 1885, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1243, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 707, in read_version_info
    raise PyCentralError, "package has no field Python-Version"


and finishing with

dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-reportlab:
 python-reportlab depends on python-central (>= 0.6); however:
  Package python-central is not configured yet.
dpkg: error processing python-reportlab (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hpijs:
 hpijs depends on hplip (>= 2.8.2-0ubuntu8); however:
  Package hplip is not configured yet.
dpkg: error processing hpijs (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.


as you can see -- a lot of problems.

Bye
Rob

---

### Post by Pumalite on 2008-07-05
Thanks. Good luck!

---

