---
title: "Won't Compile; X11 Dependencies; I have all packages though?"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by bttf on 2011-11-20
Hello,

I am trying to build some drivers for a wacom tablet; I'm running an autogen.sh script right now, and it breaks at this:

```
checking for X11... no
configure: error: Package requirements (x11 xi xrandr xinerama) were not met:

No package 'xinerama' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables X11_CFLAGS
and X11_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Thing is, I've downloaded all the x11 packages I could find that are related to the ones listed in the output message... Here is a list of what I've got so far:

x11-common
x11-xserver-utils
libxinerama1
libxi6
x11-utils
x11proto-xinerama-dev
libdmx-dev

What should I do?
Thanks,
bttf

---

### Post by oldos2er on 2011-11-20
Which version of Ubuntu are you using?

I think the package you need is libxinerama-dev

---

### Post by Favux on 2011-11-20
Hi bttf,

The needed libraries are listed in either the [LinuxWacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") or the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by bttf on 2011-11-20
> **oldos2er said:**
> Which version of Ubuntu are you using?

I think the package you need is libxinerama-dev

That was it, thank you!

I'm using Ubuntu 10.10, and am following this to fix the input on my wacom tablet:
[https://answers.launchpad.net/magick-rotation/+faq/1603](https://answers.launchpad.net/magick-rotation/+faq/1603)

---

