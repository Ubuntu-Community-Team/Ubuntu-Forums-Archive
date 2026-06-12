---
title: "Problem compiling Banshee"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by frangoitia on 2010-04-18
When trying to compile the last version from source, it gives me the following error:


checking for GDATASHARP... configure: error: Package requirements (gdata-sharp-core >= 1.4
			gdata-sharp-youtube >= 1.4) were not met:

No package 'gdata-sharp-core' found
No package 'gdata-sharp-youtube' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GDATASHARP_CFLAGS
and GDATASHARP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Any help would be appreciate it.
Thanks in advance.

---

### Post by tom4everitt on 2010-04-18
If you run 

sudo aptitude search gdata

you will get a list of packages that you probably need to install. I'm not sure exactly which are required, but packages ending with -dev are usually interesting when compiling.

So install what seems appropriate, and then try compiling again.

---

### Post by frangoitia on 2010-04-18
> **tom4everitt said:**
> If you run 

sudo aptitude search gdata

you will get a list of packages that you probably need to install. I'm not sure exactly which are required, but packages ending with -dev are usually interesting when compiling.

So install what seems appropriate, and then try compiling again.
Yes, already ve done that and didnt work.
Thanks you anyway.

---

### Post by oldos2er on 2010-04-18
Banshee has both a stable and unstable PPA: [https://launchpad.net/~banshee-team/+archive/ppa](https://launchpad.net/~banshee-team/+archive/ppa)

---

### Post by mingetch on 2011-04-18
In my case the libgdata missing package was solved with [FONT="Courier New"]libgdata-cil-dev[/FONT] pagckage, next are the other dependecies i needed to install in my system
```
aptitude install mono-2.0-devel monodoc-banshee-manual libndesk-dbus-glib1.0-cil-dev libgstreamer-plugins-base0.10-dev libboo-cil-dev   libgdata-cil-dev gtk-sharp2 libsqlite3-dev libgconf2.0-cil-dev libmtp-dev libgpod-cil-dev libipodui-cil-dev libipod-cil-dev libmono-zeroconf-cil-dev
```
Using: Ubuntu 10.10 x86_64 GNU/Linux

cheers

mingetch

---

