---
title: "Python bug Jaunty?"
date: 2009-03-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hellsgator on 2009-03-05
python-opencv:
  Depends: python (<2.6) but 2.6.1-0ubuntu3 is to be installed

Been getting this message for while now. Any fix known yet? :(

---

### Post by gwitt on 2009-03-09
Hi hellsgator

I've got the same problem, but no solution, yet.
Just hoping that this phantastic new release will be maintained soon.
I installed the (buggy) 4.4 GB DVD jaunty x86_64 build, burned it on a 8 GB DVD and was amazed how good the installation went.

All my Toshiba A210 notebook features worked out of the box. Needed just to activate the atheros wlan driver.

Only the ATI Radeon 2400 HD driver has no hardware 3D features.

If just that nasty pyhton bug wasn't there .... :(

But they fixed everything in the previous releases, why shouldn't they succeed in Jaunty ? :P

Hope dies at last!

---

### Post by ssam on 2009-03-09
please file a bug
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by DougieFresh4U on 2009-03-10
> **hellsgator said:**
> 
  Depends: python (<2.6) but 2.6.1-0ubuntu3 is to be installed

Been getting this message for while now. Any fix known yet? :(
 Been getting the same dependency error trying to install **'python-4suite-xml'**.
It starts out trying to install **'gnome'** which depends on **'serpentine'** which depends on** 'python-4suite-xm'**
Any one else having issue trying to install **'gnome'**?

---

### Post by wgrant on 2009-03-10
We are well over a month from release - you can expect lots of things to be broken!

In this case, it's because we're currently part way through transitioning from Python 2.4 and 2.5 to 2.5 and 2.6. This could take up to a couple of weeks to finish off.

---

### Post by www.rzr.online.fr on 2009-03-27
> **wgrant said:**
> 
In this case, it's because we're currently part way through transitioning from Python 2.4 and 2.5 to 2.5 and 2.6. This could take up to a couple of weeks to finish off.

Where is this reported on LP ?

Thanx
-- 
[http://rzr.online.fr/q/python](http://rzr.online.fr/q/python)

---

### Post by joewski on 2009-03-27
> **ssam said:**
> please file a bug
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Since pythons down this system doesn't work anymore!

---

### Post by wgrant on 2009-03-27
The issue that this thread is about doesn't affect any heavily-used packages any more. However, a new, much more sinister issue surfaced a couple of hours ago.

Are you finding PyGTK apps (including Update Manager and Apport) to be broken? If so, either downgrade python2.6 and python2.6-minimal or wait a couple of hours until the fix is available. Once the problem was discovered, access to the broken packages was revoked - no upgrades from the main mirror should be breaking any more systems.

---

### Post by BUGabundo on 2009-03-27
please see bug [https://bugs.launchpad.net/ubuntu/+source/python2.6/+bug/349467](https://bugs.launchpad.net/ubuntu/+source/python2.6/+bug/349467)

---

