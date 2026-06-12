---
title: "(Lucid) apport unusable due to lazr.restfulclient"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by jbatista on 2010-12-31
I'm not entirely sure where this bug might be coming from. I suspect that my Python installation is somehow mucked up but many other things are functional.

I first identified it when I attempted to use **apport-bug**: in the console I got the message 
```
Could not import module, is a package upgrade in progress? Error: No module named restfulclient.errors
```

I traced to an import from lazr.restfulclient in file /usr/share/pyshared/launchpadlib/errors.py. Running the single import line in this file yields:
```
Python 2.6.5 (r265:79063, Apr 16 2010, 13:57:41) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from lazr.restfulclient.errors import *
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named restfulclient.errors
```
So, commenting that import line from that file, the apport-bug console execution gives **another** message:
```
Could not import module, is a package upgrade in progress? Error: cannot import name HTTPError
```
So it seems to revolve around lazr.restfulclient ...

But the /usr/share/pyshared/lazr/restfulclient/errors.py file **is** present in my system (package python-lazr.restfulclient)...
```
$ LANG=C dpkg -l *launchpad* *lazr* *apport*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
ii  apport                      1.13.3-0ubuntu2             automatically generate crash reports for debugging
un  apport-cli                  <none>                      (no description available)
ii  apport-gtk                  1.13.3-0ubuntu2             GTK+ frontend for the apport crash report system
un  apport-kde                  <none>                      (no description available)
un  apport-retrace              <none>                      (no description available)
ii  apport-symptoms             0.9                         symptom scripts for apport
ii  dh-apport                   1.13.3-0ubuntu2             debhelper extension for the apport crash report system
ii  firefox-launchpad-plugin    0.4                         Launchpad firefox integration
ii  launchpad-integration       0.1.35                      launchpad integration
un  liblaunchpad-integration0   <none>                      (no description available)
ii  liblaunchpad-integration1   0.1.35                      library for launchpad integration
un  liblaunchpad-integration1-c <none>                      (no description available)
ii  liblaunchpad-integration1.0 0.1.35                      CLI bindings for liblaunchpad-integration
ii  python-apport               1.13.3-0ubuntu2             apport crash report handling library
un  python-apport-utils         <none>                      (no description available)
ii  python-launchpad-integratio 0.1.35                      library for launchpad integration
ii  python-launchpad-integratio 0.1.35                      library for launchpad integration (debug extension)
ii  python-launchpadlib         1.6.0-0ubuntu1              Launchpad web services client library
un  python-lazr-restfulclient   <none>                      (no description available)
un  python-lazr-uri             <none>                      (no description available)
ii  python-lazr.batchnavigator  1.0-0ubuntu1                A helper to navigate batched results in a web page
ii  python-lazr.delegates       1.1.0-0ubuntu1              Easily write objects that delegate behavior
ii  python-lazr.enum            1.1.2-0ubuntu3              Enums with zope.schema vocabulary support and database-friendly conven
ii  python-lazr.lifecycle       1.0-0ubuntu1                Richer lifecycle events API
ii  python-lazr.restful         0.9.19-0ubuntu1             Publish Python objects as RESTful resources over HTTP
ii  python-lazr.restfulclient   0.9.11-1ubuntu1.1           client for lazr.restful-based web services
ii  python-lazr.uri             1.0.2-1                     library for parsing, manipulating, and generating URIs
un  python2.6-launchpad-integra <none>                      (no description available)
```

I'm really confused about how I might attempt to solve this problem! :( I've tried to install/uninstall the apport packages, tried to reinstall  lazr, I've tried doing a **dpkg-reconfigure python-central**, etc etc... to no avail. Everything else seems to be functional except for this.

I **know** that apport is working in other systems: I've tried and it works. But it's not working on this one (Lucid with architecture amd64) and I don't even know where I should look at.

I'm at my wit's end here. I'll provide further information on request that will help diagnose this problem. Thank you in advance!

---

### Post by jbatista on 2010-12-31
To answer my own question:

It turns out that (at the time of this writing) two Python packages were keeping apport from running, giving the 
[LIST]
[*][python-lazr.batchnavigator]("http://packages.ubuntu.com/lucid/python-lazr.batchnavigator") - bug report [bug #696075]("https://bugs.launchpad.net/ubuntu/+bug/696075")
[*][python-lazr.delegates]("http://packages.ubuntu.com/lucid/python-lazr.delegates") - [bug #696134]("https://bugs.launchpad.net/apport/+bug/696134")
[/LIST]
To me it's not clear *why* these packages are giving this problem against python-lazr.restfulclient.

The use of [strace]("http://packages.ubuntu.com/lucid/strace") was instrumental in trying out different installations (against a known working installation) to see which files/directories were being accessed. Hopefully this will give an idea for other users who in the future are faced with similar problems; basically it involves running the program name prepended with strace, e.g.:
```
strace *program* 2>strace.log
```
when wanting to test *program*. Of course, this will produce an ample output. The real work comes then from figuring out *where* the problem happens...

---

