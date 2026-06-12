---
title: "Show Proprietary Applications In Add/Remove Applications"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by QuantumG on 2007-06-29
One thing that has always annoyed me about the Add/Remove Applications applet in Ubuntu was the inability to list all the proprietary packages available. Your filter options are: 

```

All available applications
All Open Source applications
---
Supported Ubuntu applications
Third party applications
---
Installed applications 

```

As one might expect, this applet is written in python. The scripts are in /usr/share/pycentral/gnome-app-install/site-packages/AppInstall/ and one of the files is Menu.py and it has this little nugget in it: 

```

# possible filter states for the application list
( SHOW_ALL,
  SHOW_ONLY_SUPPORTED,
  SHOW_ONLY_FREE,
  SHOW_ONLY_MAIN,
  SHOW_ONLY_PROPRIETARY,
  SHOW_ONLY_THIRD_PARTY,
  SHOW_ONLY_INSTALLED
 ) = range(7)

```

Ohhh, what's that? SHOW_ONLY_PROPRIETARY you say? The feature I want appears to be implemented but there's simply no entry in the combo box for it! Apply this patch and there will be: 

```


--- /usr/share/pycentral/gnome-app-install/site-packages/AppInstall/AppInstall.py.original      2007-06-29 20:48:37.000000000 +1000
+++ /usr/share/pycentral/gnome-app-install/site-packages/AppInstall/AppInstall.py       2007-06-29 20:48:52.000000000 +1000
@@ -191,6 +191,11 @@

                "restricted by law or copyright, "
                "unsupported by Canonical Ltd. or not part of Ubuntu"),
              SHOW_ALL),

+            (_("All Proprietary applications"), False,
+             _("Show all applications which can not be freely used, "
+               "modified and/or distributed. This includes a large "
+               "variety of non-free applications and codecs."),
+             SHOW_ONLY_PROPRIETARY),
             (_("All Open Source applications"), False,
              _("Show all Ubuntu applications which can be freely used, "
                "modified and distributed. This includes a large " 

```

And now it works! I count 52 packages that are non-free. Compare this to when I do "Third party applications".. it lists 2 (vmware player and server).

Enjoy.

---

### Post by satx on 2007-06-30
Good stuff!

---

