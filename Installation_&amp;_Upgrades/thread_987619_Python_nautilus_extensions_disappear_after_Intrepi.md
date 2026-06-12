---
title: "Python nautilus extensions disappear after Intrepid upgrade"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by colonelPannick on 2008-11-19
I've written a few python extensions to nautilus over the last couple of years and now suddenly after upgrading to Intrepid they have all ceased to function. Has the location they should be placed in changed? I have them in ~/.nautilus/python-extensions which is still the location in the examples included in python-nautilus package.

---

### Post by colonelPannick on 2008-11-21
No they haven't.

What seems to have happened is that the method for testing listed in */usr/share/doc/python-nautilus/examples/README* to set up a private instance of nautilus no longer works and so I wasn't seeing the debug messages I was adding. Instead you need to kill the instance of nautilus running since log in with *nautilus --quit* and then start nautilus in a console with *nautilus --no-desktop* and all the debug output is there to be seen and I know now why my extensions stopped working (a changed mime type).

---

