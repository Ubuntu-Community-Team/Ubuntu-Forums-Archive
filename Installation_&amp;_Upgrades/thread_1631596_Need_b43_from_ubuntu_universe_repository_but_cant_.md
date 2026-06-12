---
title: "Need b43 from ubuntu universe repository but cant go online"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by sbryant31 on 2010-11-26
I'm trying to install the wifi drivers on my compaq mini. I got this when I try to install my bcmwl-kernel-source.

Building initial module for 2.6.35-22-generic
/usr/sbin/dkms line 35: patch: command not found
Error! Application of patch 001-MODULE_LICENSE.patch failed.
check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build for more information.
traceback (most recent call last):
File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
report.write(open(apport.fileutils.make_report_pat h(report),'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/bcmwl -kernel-source.0.crash'

I don't have access to the internet, so I need to know exactly which things I must install and uninstall. My package manager is being a real bear of a problem, so if someone can tell me what I need to install to fix this error that would be great.

---

### Post by kerry_s on 2010-11-26
i think for your version it's on the installer.

put the installer in an open it, go to pool-> restricted-> b-> bcmwl

double click on the deb file.

you'll most likely need to reboot for it to load.


i'm on 64bit but yours should look something like this.

---

### Post by Elfy on 2010-11-26
Closed - forum hiccup - duplicate - [http://ubuntuforums.org/showthread.php?t=1631638](http://ubuntuforums.org/showthread.php?t=1631638)

---

