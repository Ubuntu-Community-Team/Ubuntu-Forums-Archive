---
title: "For those of you whom OpenOffice fails to upgrade, this may help."
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by marshall.robert on 2008-06-29
i know there are a few posts like this, but none actually address this issue i was having...

here is the error:

E: /var/cache/apt/archives/openoffice.org-writer_1%3a2.4.1-1ubuntu1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libsw680li.so')

and after that it quits updating.

i had to completely remove OpenOffice to install the rest of the updates....

Now i have installed OpenOffice again, for the acception of Writer which keeps throwing that error above.

so i pop open a terminal and type "sudo apt-get clean" which gets rid of all the downloaded packages, thus freeing up disk space, and forcing apt to download a new one.

then i type "sudo apt-get install openoffice.org-writer" and it installs, yay!

hope this helps

-rob

---

