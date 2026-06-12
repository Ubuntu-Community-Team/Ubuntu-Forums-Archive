---
title: "[SOLVED] `evolution-common' contains empty filename"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by MauriceGoodf on 2008-06-03
Any time I try to upgrade a package, I get a message saying something like "E: /var/cache/apt/archives/evolution-common_2.22.1.1-0ubuntu3_all.deb: files list file for package `evolution-common' contains empty filename" and the installation fails.

The history is that I tried to load Google Earth.  It didn't work.  The clock applet would no longer run (may be co-incidence). I tried to use the Synaptic Package Manager to reload the GNOME panel, then the panel and its data.  GNOME panel failed with the above message (except for the package name).  Automatic upgrades also fail for the same reason.  I even tried to reload evolution-common and got the variant of the error message seen above.

Any ideas as to what I've done wrong and how to resolve it?

Thanks,

Maurice

---

### Post by MauriceGoodf on 2008-06-06
SOLVED

From a terminal, 

cd /var/lib/dpkg/info
sudo mv evolution-common.list evolution-common.bak

and then run System->Administration->Update Manager

and it all worked

Now, if only I could find out how to change the name of this thread to say that it is solved...

---

