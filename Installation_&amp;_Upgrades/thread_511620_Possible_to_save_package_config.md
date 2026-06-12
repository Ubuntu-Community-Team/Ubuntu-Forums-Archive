---
title: "Possible to save package config?"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by Timtro on 2007-07-28
Hi all,

I believe I may have broken something small on my Ubuntu install. If it comes down to it, and I decide it's just easier to fresh install, Is there any way for me to save the selected packages so that I could simply 'restore' a fresh install with all of my currently selected (non-default) packages?

This way, I only have to reinstall stuff which I installed which isn't in the repos. It seems like it shouldn't be a problem. Also, I have '/home' mounted to a separate partition. Will I be able to 'import' these users?

Thanks,


Tim.

---

### Post by logos34 on 2007-07-28
Try **APTonCD**:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
[http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html](http://linuxhelp.blogspot.com/2006/11/aptoncd-create-backup-of-all-packages.html)

It will backup to cd or dvd all the deb pkgs in /var/cache/apt/archives directory (which is where everything you downloaded and/or installed is stored--the default pkgs from the install cd as well stuff added later from synaptic/apt-get.  It will then ask you about any debs you installed separately (which you'll have somewhere in /home or /tmp. 

Be sure to make a metapackage, so that when you restore you just start with that and it will drag everything back into your new install, handling all the dependencies.

---

### Post by Timtro on 2007-08-01
Thanks, I'll give this  a try. Cheers mate.

---

