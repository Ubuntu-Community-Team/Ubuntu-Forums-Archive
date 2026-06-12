---
title: "ppa-purge can not find package list for PPA"
date: 2015-06-16
forum: Installation &amp; Upgrades
---

### Post by jim_osborn on 2015-06-16
My file
 
/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_brightness-controller_ubuntu.list

contains the following:

deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/brightness-controller/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/brightness-controller/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

I've tried every combination/permutation I can think of of "private-ppa.launchpad.net", "commercial-ppa-uploaders" and "brightness-controller" with the -p and -s options (and without either of those options) to ppa-purge, but it always fails with a message like this:

Warning:  Could not find package list for PPA:  commercial-ppa-uploaders/brightness-controller ppa

with the details of the hapless PPA depending on my invocation of ppa-purge.

In my file

/var/lib/apt/lists/private-ppa.launchpad.net_commercial-ppa-uploaders_brightness-controller_ubuntu_dists_trusty_Release

there is a line:

Origin: LP-PPA-commercial-ppa-uploaders-brightness-controller

but I can't think of any way to use that info to solve this problem (simply pointing ppa-purge at it gives the same error).  I can't remember how I came to add this ppa, and can't seem to find a reference to it, so I guess I'm stuck with the info in my computer.

Can someone more familiar with ppa-purge than me suggest how I can purge this ppa?

Thanks

jimo

---

### Post by dino99 on 2015-06-16
ppa-purge need a conventional address, like  ppa:******/******

 [http://manpages.ubuntu.com/manpages/trusty/man1/ppa-purge.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/ppa-purge.1.html)

---

### Post by mc4man on 2015-06-16
private ppa builds  like that are only used thru software-center. So if you want to remove the package from it use software-center.
for ref. - [https://apps.ubuntu.com/cat/applications/brightness-controller/](https://apps.ubuntu.com/cat/applications/brightness-controller/)

If it's listed in sources then open Software & Updates > Other. If you see it highlight, click remove
Edit; as in screen

---

### Post by jim_osborn on 2015-06-16
Thanks, mc4man. Software-center was able to remove the brightness-controller, which I might actually want to use someday, but it left the PPA untouched in /etc/apt/sources.list.d/..., which is my primary concern.  I'm trying to eliminate as many PPAs as possible while I try to get my installation under control.  I suppose I could trust that software-center's removal of BC did all the work that ppa-purge would have done, and I could simply comment out the lines in the .list and .list.save files under /etc/apt/sources.list.d/ but I'd prefer to rely on apt to purge things in case there are other adjustments to be made.  Or I could try to use add-apt-repository --remove, but if I couldn't point ppa-purge at that PPA, I worry that I could spend tens of hours on another dead end.

---

### Post by jim_osborn on 2015-06-16
> **dino99 said:**
> ppa-purge need a conventional address, like  ppa:******/******

 [http://manpages.ubuntu.com/manpages/trusty/man1/ppa-purge.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/ppa-purge.1.html)

I've spent somewhere between ten and thirty hours going over that manpage.  I find the information from ppa-purge -h more helpful than the manpage in that it gives three examples.  Most of my time has been spent trying to fit the PPA in question into those examples.
I don't understand what you mean by "a conventional address, like ppa:******/******"  Would you care to substitute the data from the PPA I posted into your "conventional address" so that I might understand what you mean?

---

### Post by mc4man on 2015-06-17
In the case of these commercial apps you'd probably  need to look for yourself to see if their install included other packages that would no longer be needed after removing the commercial app. Don't expect that their install & removal to be treated like normal packages.
(- nor are these really ppa's 

So in this case,  brightness-controller, it  may of installed python-wxgtk2.8  **If so** it would be marked as 'automatically' installed but would not show up as auto removable after removing brightness-controller. You'd need to remove  python-wxgtk2.8 manually yourself.
Whether this is the deal with all the commercial apps don't know as rarely have used/installed any..

---

