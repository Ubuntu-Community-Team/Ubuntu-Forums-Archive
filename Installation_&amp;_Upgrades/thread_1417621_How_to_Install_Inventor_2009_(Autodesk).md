---
title: "How to Install Inventor 2009 (Autodesk)"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by Gnimmelf on 2010-02-27
Hi 
I am a rookie running Ubuntu, and would like to know how to install Inventor 2009 on this system. 
Does anyone have expiriense with that ??
regards Gnimmelf

---

### Post by Steven_B on 2010-02-27
When I last checked, Autodesk doesn't support Linux at all.  Your choices are to try to install Inventor in Wine, or to use a Windows in a virtual machine.
With Wine, your chances aren't good:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5719]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=5719")

With [VirtualBox]("http://virtualbox.org"), or another virtual machine the trick is getting hardware graphics acceleration.  It's possible to use software OpenGL, but it's painfully slow if you have more than a few parts.

---

