---
title: "upgrade help"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by moore.bryan on 2006-09-23
*my "very smart" wife decided to play with my linux... not sure why she suddenly made that choice, but... and for some reason she decided to try the edgy upgrade.  now, it tells me xserver-xorg isn't installed.  i've seen other posts about that, but there are other problems.  namely, i can't get onto the internet because my eth0 isn't being recognized.  so, i can't apt-get or aptitude.  so now i'm sitting in knoppix (sorry, it's so much quicker than the ubuntu livecd) trying to solve the problem, but i'm not even sure where to start.  help!*

---

### Post by chicken101 on 2006-09-23
I would suggest reverting back to dapper.  Go into synaptic and change all the repositories so that the word "edgy" is replaced by "dapper".

You could also do:
> sudo gedit /etc/apt/sources.list

to change things a little faster. 

You could probably procure a copy of the defualt dapper repos list as well.

---

### Post by moore.bryan on 2006-09-23
*that's just it... i can't get to the internet to get any packages...*

---

### Post by moore.bryan on 2006-09-23
*could i download xserver-xorg through knoppix, copy it to my hd and load it from there?  or is it a better alternative to download the alternate edgy iso, burn it, and run the upgrade from that?  if the latter's best, how do i manually upgrade from a cd without destroying all my files?*

---

### Post by K.Mandla on 2006-09-23
Do you have access to an alternate/install CD? You might be able to fix it with that.

---

### Post by K.Mandla on 2006-09-23
> **moore.bryan said:**
> if the latter's best, how do i manually upgrade from a cd without destroying all my files?
I have no idea if this would work, but if it were me I would ...

[LIST=1]
[*]Get your hands on a Dapper alternate/install CD (I think I would avoid Edgy)
[*]Boot into your broken system
[*]Change sources.list to read only Dapper repositories
[*]Put the CD in the drive and *sudo apt-add cdrom*
[*]I would *sudo aptitude clean* to dump the edgy packages
[*]Then *sudo aptitude update* and try to *sudo aptitude upgrade* from there.
[/LIST]
Again, I don't know if that would work. But that would be my plan.

---

### Post by moore.bryan on 2006-09-23
[I]k.mandla...
thanks for the advice... i'm going to try the edgy alternate cd (since i'm not sure i can screw it up much more than it already is) and if that doesn't work the dapper.  i hope the community keeps their fingers crossed for me...
[/I]

---

### Post by K.Mandla on 2006-09-23
Right on. Let us know how it goes. Good luck!

---

### Post by moore.bryan on 2006-09-23
[I]alright... neither the dapper nor edgy cd's worked/helped, but i was able to reinstall xserver-xorg from its deb.  then, when i got back into ubuntu, i tried to follow the howto in the forum for edgy; namely, changing every dapper instance in sources.list to edgy, then ```
sudo aptitude update && sudo aptitude upgrade
``` after it worked for an hour or so, i get this message at the end > Errors were encountered while processing:
 acpid
 acpid-support
localepurge: Disk space freed in /usr/share/locale: 5512K
E: Sub-process /usr/bin/dpkg returned error code (1)
A package failed to install.  Trying to recover:
Setting up acpid (1.0.4-5ubuntu4) ...
 * Loading ACPI modules...
 * Starting ACPI services...
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support couple of questions:
(1) is this important?
(2) if so, why; what does it do?
(3) is this a common error?
i've upgraded before (breezy --> dapper) and didn't have this problem... thanks, in advance all.
-------------------------------------
i looked at launchpad and it seems as though there are different modules for each kernel... i'm running 2.6.17.11 and there isn't one on launchpad for it... could that be my issue?
[/I]

---

### Post by moore.bryan on 2006-09-24
*alright, now after rebooting and fixing the grub menu.lst that edgy screwed up for some reason by changing my root dir to some illogical sequence of #'s and letters, i get a "black screen of death" with simply a cursor in the upper left.  i reedited the menu.lst, removed "quiet" and "splash" from the kernel commands and found it hanging on > usb 1-1: configuration #1 chosen from 1 choice any new ideas?*

---

### Post by moore.bryan on 2006-09-25
*alright, so no matter what i did, i couldn't go back to dapper or go up to edgy... i had to run a complete reinstall with dapper; pain in my... my new problem is menumaker won't run... why can't i just be brilliant?  :-)*

---

### Post by krisek on 2006-09-26
> **moore.bryan said:**
> [I]... after it worked for an hour or so, i get this message at the end  couple of questions:
(1) is this important?
(2) if so, why; what does it do?
(3) is this a common error?
i've upgraded before (breezy --> dapper) and didn't have this problem... thanks, in advance all.
-------------------------------------
[/I]

Hi, 

did you find the solution for this acpid post-installation problem? I have exactly the same problem.

Chris

---

### Post by moore.bryan on 2006-09-26
> **krisek said:**
> Hi, 

did you find the solution for this acpid post-installation problem? I have exactly the same problem.

Chris
*unfortunately, no... ubuntu wouldn't respond for me at all, to the point i couldn't even get a bash prompt.  i formatted the whole drive and reinstalled from scratch to dapper.  i've read this is a known problem, though and if some suggest reinstalling acpid and acpi-support from dapper could work.*

---

