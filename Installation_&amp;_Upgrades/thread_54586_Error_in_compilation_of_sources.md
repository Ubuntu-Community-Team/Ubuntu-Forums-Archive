---
title: "Error in compilation of sources"
date: 2005-08-05
forum: Installation &amp; Upgrades
---

### Post by cnayak on 2005-08-05
Whenever  I try to compile XMMS, Xine or any other application from the sources, it fails giviing this error message:

[I]
checking for glib-config... no
checking for GLIB - version >= 1.2.2... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***


  [/I]

 I installed glib-2.6.6 but the problem persisted. Any suggestions?

---

### Post by dave9191 on 2005-08-05
You will need the development lib package (one ending in -dev) which contains the source code for it, which is required to compile xmms. 

Dave

---

### Post by cnayak on 2005-08-05
Where do I unzip the package?

---

### Post by dave9191 on 2005-08-05
Unzip the package? You should be able to get glib and the -dev libaries through synaptic. If you downloaded the packages yourself, it should come with a README file. 

Dave

---

