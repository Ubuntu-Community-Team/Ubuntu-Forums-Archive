---
title: "Broken Packages in synaptic"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by driebel on 2010-05-07
During my recent upgrade from 8.04 to 10.04, I got a few error messages concerning the flashplugin-nonfree not installing correctly.  A user named carlee helped me get flash working over on the absolute beginner forum, but I've got a related problem still unresolved.  Update manager is convinced that my perfectly working flash installation is broken, and insists I update it.  However, the update fails every time, telling me 

E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

Opening synaptic, I cannot select the reinstall option for the plugin.  Removal and complete removal are my only options, and both give the above error.  More problematic, I cannot de-select the flash plugin entirely.  It MUST be part of any other package update through synaptic (if I wanted to re-install avant window navigator, for example).  And since the flash removal operation fails, synaptic is effectively non-operational.

How can I convince my update manager that my fully operational flash is just fine the way it is?

Dave

---

### Post by davidmohammed on 2010-05-07
if you can outline what commands you used to install that would be useful.

At a guess have you tried sudo apt-get -f remove flashplugin-nonfree

followed by sudo apt-get purge flashplugin-nonfree

followed by sudo apt-get install flashplugin-nonfree

---

### Post by driebel on 2010-05-07
To get the plugin working, I used the 64bit GUI installer written by carlee.  The link is in her signature file, visible in this thread:

[http://ubuntuforums.org/showthread.php?t=1475441](http://ubuntuforums.org/showthread.php?t=1475441)

Specifically, I ran the executable adobe_flash_installer-ubuntu-64bit, which executes several commands, not all of which I caught.

Would you recommend running the commands you listed, just to "clear" the update manager?

---

### Post by davidmohammed on 2010-05-07
ok looks like a messy approach you've taken.  Dont try my suggestions - likely to break more than fix.

Hope someone who's tried carlee's method has a better idea... sorry

---

### Post by driebel on 2010-05-07
I might get messier.  I found this, where some reports the exact same error message for a different package:

[http://ubuntuforums.org/showthread.php?t=813809](http://ubuntuforums.org/showthread.php?t=813809)

I'm very close to trying it...

Also, I defend this installer routine idea.  Getting 64-bit flash to work has been a hassle on Unbuntu for awhile, and having a simple script that dumbs down a ~4 step process for the super-noobs (like yours truly) seems like a good idea.  Just my thoughts on the subject :)

---

### Post by rsanchez1 on 2010-05-07
I had a similar problem when I was upgrading to 10.04 from 8.04 with the same package. It led to the problem I'm having, which I described in this post: [http://www.backports.ubuntuforums.org/showthread.php?p=9250851&posted=1#post9250851](http://www.backports.ubuntuforums.org/showthread.php?p=9250851&posted=1#post9250851)

If someone could help me with that, I would appreciate it.

I did manage to get the package to correctly update by doing the method specified in this blog post: [http://itechlog.com/linux/2008/12/18/fix-broken-package-ubuntu/](http://itechlog.com/linux/2008/12/18/fix-broken-package-ubuntu/)

Basically, you just delete the entry for the flash plugin package from dpkg status, and then if you do apt-get install on the same package it will install with no problems.

---

