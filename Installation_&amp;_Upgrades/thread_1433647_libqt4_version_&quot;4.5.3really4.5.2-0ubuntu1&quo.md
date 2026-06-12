---
title: "libqt4 version: &quot;4.5.3really4.5.2-0ubuntu1&quot;. Why?"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by edantes on 2010-03-19
Is this funny  version number a good idea? 

I tried to install a package from Debian Sid on Karmic and it requires   version >= 4:4.5.2 for the qtlib4 packages.  Which would be fine with the 4.5.2 in Karmic, except that the dependency test fails.

Well, I installed the package ignoring the dependencies.  It works fine, except that Package Manager keeps complaining and attempting to "fix" the broken (not really!) package.

Is there a way of making the manager ignore this?

A little background:

The QtOctave package available in the Karmic repositories is outdated and dependent on an old version of Octave.

I had Octave 3.2 already installed and downloaded the QTOctave 0.8.2 package from here:

[http://packages.debian.org/sid/amd64/qtoctave/download](http://packages.debian.org/sid/amd64/qtoctave/download)

Then, installed it by brute force:

sudo dpkg --ignore-depends=libqt4-network,libqt4-script,libqt4-sql,libqt4-svg,libqt4-xml,libqtcore4,libqtgui4 -i qtoctave_0.8.2+dfsg-2_amd64.deb

---

### Post by jon.mithe on 2010-04-20
+1 for the oddness. I tried installing hedgewars which needs 4.5.3 and fails.  Looking into removing it and installing 4.5.3 but not too sure what this will break...  need to find that out first...  Or maybe wait until 10.04, fingers crossed they'll have the proper version in there.

---

