---
title: "Problem during recent updates"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by Bill_Zaumen on 2007-02-08
When I ran update manager today, it told me to run
   sudo apt-get dist-upgrade

and that program reports:

The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

update-manager now reports

Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.

and lists
        linux-image-386
        linux-restricted-modules-386

I can't seem to make this message go away.  Running

      sudo apt-get dist-upgrade

doesn't help, nor does using the synaptics package manager function.

Any ideas as to what to do?

Thanks

---

### Post by marko_4454 on 2007-02-08
theres a post about it..

[http://ubuntuforums.org/showthread.php?t=356408&highlight=fix+broken+packages](http://ubuntuforums.org/showthread.php?t=356408&highlight=fix+broken+packages)


It's called:  WARNING RE LATEST UPDATE: Broken dependency: linux-image-generic

---

