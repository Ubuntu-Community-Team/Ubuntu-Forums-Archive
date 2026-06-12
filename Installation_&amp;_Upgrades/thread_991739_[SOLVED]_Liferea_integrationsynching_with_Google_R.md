---
title: "[SOLVED] Liferea integration/synching with Google Reader"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by gb5757870 on 2008-11-24
Once of the last remaining hurdles I have for using Linux solely is using a RSS program that synch's to a web-based reader. I found a thread here that mentioned a version of Liferea that can do this with Google Reader. 

I have downloaded the version that has this integration off the Liferea sourceforge page but when I run the ./configure I get the following:

[B]checking for PACKAGE... configure: error: Package requirements (	gtk+-2.0 >= 2.10.0
		glib-2.0 >= 2.16.0
		pango >= 1.4.0
		gconf-2.0 >= 1.1.9
		libxml-2.0 >= 2.6.27
		libxslt >= 1.1.19
		sqlite3 >= 3.3
		gmodule-2.0 >= 2.0.0
		libglade-2.0 >= 2.0.0
		libcurl >= 7.15.0) were not met:

No package 'gtk+-2.0' found
No package 'glib-2.0' found
No package 'pango' found
No package 'gconf-2.0' found
No package 'libxml-2.0' found
No package 'libxslt' found
No package 'sqlite3' found
No package 'gmodule-2.0' found
No package 'libglade-2.0' found
No package 'libcurl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/B]

From what I can tell at least a few of these packages aren't even available. Has anyone actually got this working?

** Update **
Turns out the version of Liferea in the repositories actually supports this already. Closing thread

---

### Post by lakersforce on 2008-11-24
Quite often the packages needed does not have the exact same name, but one similar.

---

