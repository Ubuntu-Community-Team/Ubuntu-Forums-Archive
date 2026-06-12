---
title: "OpenGL dev with GLX"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by subi211 on 2007-10-01
I hate asking this question, because it must be fairly common, but I can't find the answer!

I'm trying to use Eclipse to port a GL renderer from Windows to Linux.  As a reference, I'm using the Nehe tutorials ported to Linux/GLX (I didn't want to use GLUT for various reasons).

I got them compiling fine using Fedora 6, but I just didn't like Fedora that much, so I switched to Ubuntu on the recomendation of a couple of friends.  But, its seems that Fedora is five times bugger than Ubuntu for a reason.  :)

I can't find the GL, GLX or X dev stuff anywhere in Ubuntu, although I did figure out how to install g++ (nice prompt from the terminal there :) ), and Eclipse (although it wasn't in the Add/Remove list like it was on Fedora).

I've followed the instructions on a few threads I've found on these forums with no real success.  At some point the sudo commands given fail with a not found error.

(you may have gathered by now that I don't really know what I'm doing when it comes to Linux :) )

So, can someone please help a poor Windows user get a C++ GLX app compiling using Eclipse on Ubuntu?  If I hit upon a nice bullet-point list of tasks I'll write it up and stick it in the wiki if it's not there already.  I'm sure I can't be the only total idiot.

Thanks.

---

### Post by subi211 on 2007-10-01
Okay, after thrashing around for a couple of hours, the question is now why, after followed the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=2044661&postcount=24"), and installing the xorg-dev package, does everything *compile* okay, but fail to link.

The answer seems to be that the packages have only given me the headers, not the libs.  But the libs aren't listed in Synaptic, even after enabling Source.

Help!  I have no idea what I'm looking for!  Surely I can't be stopped by something this simple?

---

