---
title: "Uninstalling a forcefully installed package?"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by tsiMental on 2006-09-09
I am having some troubles cause I, not knowing any better, forcefully installed project looking glass 0.9.0 - 20060907 snapshot, disregarding the error message.

Now, apt won't work. It says I have a bad package on my system, lg3d-core, which needs to be reinstalled, but it can't find any source to install it from.

I still have the downloaded .deb file, but I am unable to uninstall it or reinstall it.

Is there a way to repair apt?

I tried to uninstall using:
sudo dpkg -r lg3d-core
sudo dpkg --force-all -r lg3d-core

and reinstall using:
sudo dpkg -i lg3d-core-0.9.0.deb
sudo dpkg --force-all -i lg3d-core-0.9.0.deb

None of these gave any result at all. What do I do?

Thanks in advance.

---

