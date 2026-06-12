---
title: "dpkg: error processing system-tools-backends (--configure)"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by sreekanth27 on 2008-11-09
Hello,

I just installed UBUNTU8.10 and I do not get any sound..I have posted the issue at [http://ubuntuforums.org/showthread.php?p=6133242#post6133242](http://ubuntuforums.org/showthread.php?p=6133242#post6133242)

But the biggest issue that I am facing is this error.. Can't seem to get it work: 

###
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)
##

Please help.. I think once I get this fixed I can get back my sound back.,.

---

### Post by graabein on 2008-11-09
I've got the same problem right here. :( Also got an error about GDM or X or something while trying to fast-switch to a different user.

---

### Post by Okuryo on 2008-11-09
I get this message too:

```
$ sudo dpkg --configure -a 
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 system-tools-backends

```

This happens after a system freeze (which happened because of a graphic driver, apparently) during an update, after which I had to reset the machine.
No package manager works now.

---

### Post by charliedelong on 2008-11-09
I am also in the same boat. I have 8.10 installed on a dell latitude c600...

---

### Post by naivivvuli on 2008-11-09
yup same here. trying to install packages through terminal. output gives me error same as you guys

---

### Post by catilina on 2008-11-10
I'm also facing the same (or at least i think so) problem

> * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.27-7-generic
 system-tools-backends


---

### Post by cariboo on 2008-11-10
Have any of you tried System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages?

Jim

---

### Post by drifting on 2008-11-10
> **naivivvuli said:**
> yup same here. trying to install packages through terminal. output gives me error same as you guys

Me too, resorting to the Acronis image it took BEFORE the upgrade, thank heaven I did take one.

Would love to know how to cure this one, it suggested a DKPG --configure -a but came back with a screen full of errors, and the only one I noticed was "liboobs" :-) I wonder why that one attracted my attention? The final message said DKPG ../../src/packages.c:265: process_queue: Assertation '!que.length' failed.
Aborted 

Well that means nothing to me, so it looks like I will be going back to Hardy, and my trusty backup.

BTW I have tried this update twice via the alternate cd.

Regards Paul.

---

### Post by Dispew on 2008-11-10
I got the same error on ubuntu 8.10 after update from 
[INDENT]system-tools-backends (2.6.0-1ubuntu1) [/INDENT]
to 
[INDENT]system-tools-backends (2.6.0-1ubuntu1.1)[/INDENT]

Try to force an old version _system-tools-backends (2.6.0-1ubuntu1)_ 

This works for me

sry for the english

---

### Post by steeleyuk on 2008-11-10
I'll confirm that downgrading the package works.

> and the only one I noticed was "liboobs"  I wonder why that one attracted my attention?

+1 :D

---

### Post by Okuryo on 2008-11-11
How do I force an old version?

---

### Post by fut21 on 2008-11-11
Reinstall the package from this webpage:
[http://seclists.org/bugtraq/2008/Nov/0037.html](http://seclists.org/bugtraq/2008/Nov/0037.html)

---

### Post by busstation16 on 2008-11-11
I had this same problem, i went into synaptic marked the package for complete uninstall, uninstalled it, then reinstalled it.  It seems to have fixed the problem.

Edit 1:
Actually, after restarting i had some errors,
reinstalling liboobs (from synaptic) and running
sudo aptitude reinstall gnome-applets
has fixed all but one:
The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".

Edit 2:
ah, and the last step was of course:

sudo apt-get install fast-user-switch-applet

all appears to be well now

---

### Post by charcourt on 2008-11-22
I encountered the same problem (I believe it started after a failed graphics driver install).
I can confirm that re-installing system-tools-backends works a solution to this problem. Specifically, this is what I did:
[LIST]
[*]Completely removed "system-tools-backends" (this also removed several other packages).
[*]Re-installed "system-tools-backends".
[*]Re-installed the other packages that were removed earlier. For me this was: "fast-user-switch-applet", "gnome-applets", "gnome-system-tools", "liboobs-1-4" and "ubuntu-desktop".
[/LIST]

---

### Post by deviousjem on 2008-12-18
> **charcourt said:**
> I encountered the same problem (I believe it started after a failed graphics driver install).
I can confirm that re-installing system-tools-backends works a solution to this problem. Specifically, this is what I did:
[LIST]
[*]Completely removed "system-tools-backends" (this also removed several other packages).
[*]Re-installed "system-tools-backends".
[*]Re-installed the other packages that were removed earlier. For me this was: "fast-user-switch-applet", "gnome-applets", "gnome-system-tools", "liboobs-1-4" and "ubuntu-desktop".
[/LIST]

Can confirm that the reinstall above solves this problem.

---

### Post by nikko_bosatsu on 2008-12-23
> **fut21 said:**
> Reinstall the package from this webpage:
[http://seclists.org/bugtraq/2008/Nov/0037.html](http://seclists.org/bugtraq/2008/Nov/0037.html)
This work for Me.. the error message now gone.

---

### Post by andremk on 2008-12-25
> **deviousjem said:**
> Can confirm that the reinstall above solves this problem.

Worked as a charm! Thanks! :)

---

### Post by bobloblian on 2009-01-06
When I reinstalled the removed packages, it removed scrollkeeper.  too late for me to check now, but it may be that having scrollkeeper installed breaks system-tools-backends and the other packages, and perhaps just removing that will be sufficient?

---

### Post by Neo_The_User on 2009-01-10
the complete removal worked for me as well. Thanks all! :guitar:

---

### Post by pmorton on 2009-03-20
> **charcourt said:**
> I encountered the same problem (I believe it started after a failed graphics driver install).
I can confirm that re-installing system-tools-backends works a solution to this problem. Specifically, this is what I did:
[LIST]
[*]Completely removed "system-tools-backends" (this also removed several other packages).
[*]Re-installed "system-tools-backends".
[*]Re-installed the other packages that were removed earlier. For me this was: "fast-user-switch-applet", "gnome-applets", "gnome-system-tools", "liboobs-1-4" and "ubuntu-desktop".
[/LIST]

Worked for me.

---

