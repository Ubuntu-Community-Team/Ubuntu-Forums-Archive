---
title: "python-gst0.10: subprocess post-installation script returned error exit status 1"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by Ron Byers on 2008-06-28
I tried to upgrade to hardy last night. I received the following error message. "python-gst0.10: subprocess post-installation script returned error exit status 1"

This error resulted in a lot of stuff not being properly installed. 

I tried to force the configuration 

"sudo dpkg --configure -a --force all"

This is the result

"Setting up python-gst0.10 (0.10.11-1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-gst0.10 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libxine1 (1.1.11.1-1ubuntu3) ...
rmdir: failed to remove `/usr/share/doc/libxine1': Directory not empty
dpkg: error processing libxine1 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: gnome-app-install: dependency problems, but configuring anyway as you request:
 gnome-app-install depends on python-gst0.10; however:
  Package python-gst0.10 is not configured yet.
Setting up gnome-app-install (0.5.2.8-0ubuntu1) ...
Caching application data...
Generating mime/codec maps...

Setting up ubuntu-desktop (1.102) ...
dpkg: gxine: dependency problems, but configuring anyway as you request:
 gxine depends on libxine1 (>= 1.1.8); however:
  Package libxine1 is not configured yet.
Setting up gxine (0.5.901-1ubuntu2) ...

Configuration file `/etc/gxine/startup'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
 ==> Keeping old config file as default.

Configuration file `/etc/gxine/keypad.xml'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
 ==> Keeping old config file as default.

Configuration file `/etc/gxine/toolbar-fullscreen.xml'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
 ==> Keeping old config file as default.

Configuration file `/etc/gxine/toolbar-window.xml'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
 ==> Keeping old config file as default.

dpkg: python-gst0.10-dbg: dependency problems, but configuring anyway as you request:
 python-gst0.10-dbg depends on python-gst0.10 (= 0.10.11-1); however:
  Package python-gst0.10 is not configured yet.
Setting up python-gst0.10-dbg (0.10.11-1) ...
Setting up apturl (0.2.2ubuntu1) ...

Setting up gxineplugin (0.5.901-1ubuntu2) ...
Setting up ubufox (0.5-0ubuntu1) ...
Errors were encountered while processing:
 python-gst0.10
 libxine1"

Obviously until python-gst0.10 is properly configured my system will not function properly.  What is python-gst0.10 and how do I configure it?

---

### Post by Ron Byers on 2008-06-29
No suggestions. I just want to configure Python gst. I think Hardy was supposed to install a configuration file, but somehow it didn't happen. Help.

---

### Post by Ron Byers on 2008-07-02
I guess I am just undeserving of a reply, but I just want to know how to solve this problem.  I have seen other similar problems but they were allegedly fixed by bug fixes. Is this issue one of those Ubuntu, we won't touch code with coodies, problems I keep reading about? Somebody help, please. :confused: 

I just want to know which why the install script won't over write the local files, which local files they are talking about and why?  

Is there another forum I should visit? 

Where do I go to learn the secret handshake?

---

### Post by bijanbina on 2011-05-12
i have the same problem!

---

