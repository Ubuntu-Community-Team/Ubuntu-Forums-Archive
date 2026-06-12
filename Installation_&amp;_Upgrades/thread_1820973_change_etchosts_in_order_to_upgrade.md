---
title: "change /etc/hosts in order to upgrade?"
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by paper_brdige on 2011-08-08
I am trying to upgrade my system from 7.04 to a current version.

I now face the known problem that my machine tries to download everything from archives.ubuntu.com although it has all been moved to old-releases.

The guide I'm following suggests: "If you have this problem, you could change your /etc/host file to point archive.ubuntu.com to old-releases. Do this by running host old-releases.ubuntu.com | grep address  | awk '{print $NF"\tarchive.ubuntu.com"}' | sudo tee -a /etc/hosts."

I have tried typing that information into the command line, with no success. I opened the /etc/hosts file in emacs (using sudo) but did not see an obvious place to impliment the fix.

I know close to nothing about what I'm doing.

Thanks!

---

### Post by zvacet on 2011-08-09
Instead of doing that just install new Ubuntu release.Of course you will put your valuable files somewhere else (external HD,USB stick...)

---

