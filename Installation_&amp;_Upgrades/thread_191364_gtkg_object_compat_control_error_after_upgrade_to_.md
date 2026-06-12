---
title: "gtk/g_object_compat_control error after upgrade to dapper"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by dkuhlman on 2006-06-07
After upgrading to Kubuntu Dapper, I get this error message when I run gtk applications (for example, gedit):

gedit: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol:
g_object_compat_control

After a Web search, I've found messages in a Web about a similar error.  But, it was not clear what I should do to fix it.

Do I have a library that needs to be updated?  Is it libgtk-x11-2.0.so?  If so, what package is it in, and how do I update it?

Needless to say, if it is a gtk library, removing and reinstalling it is not a good option, because that would result in remove a *lot* of dependencies.  Or, is there a way to force an upgrade without first removing the old version?

Thanks for help.

Dave

---

