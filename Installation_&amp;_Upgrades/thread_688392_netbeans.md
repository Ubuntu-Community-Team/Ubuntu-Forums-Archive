---
title: "netbeans"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by Seeker84 on 2008-02-05
Hello everyone,

I'm trying to use Netbeans 5.5.1 from Synaptic Package Manager and it installs fine.  But then I run into this error when the program starts up:

Warning - could not install module JPDA Debugger API
	JPDA Debugger API - This module requires jpda.jar to be accessible.
This file was not found. Usually this means you are trying to run the IDE with the JRE instead of the full JDK.
If so, please use the --jdkhome command line option to specify a JDK installation.

This is after the program tries to "turning on modules..."

Any help would be greatly appreciated.  I'm using Gutsy Gibbon.  No straight ubuntu, removed KDE component, Dell Inspiron 700m, intel processor.

As a further note, Netbeans worked fine in Windows.  Trying to ween off of windows.

~Seeker

---

### Post by otep on 2008-04-10
i encountered the same problem just now. fortunately, i was able to see [this]("http://forum.java.sun.com/thread.jspa?threadID=5112119&tstart=134"). tried mystuff's solution and it worked.

---

### Post by salutis on 2008-06-25
This worked for me:
```
sudo aptitude install sun-java6-jdk
```

---

