---
title: "Anyone else having this problem?  Any Suggestions??"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Diggs808 on 2009-09-15
I installed the latest updates today, then rebooted.  Now I can only get to the CLI.  When I try 'startx' I get a message that says that it failed to load module "glx" (loader failed, 7).  



This comes from my Xorg.0.log


This is from /var/log/Xorg.0.log
 (II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: _nv000028gl
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)


I filed a LP bug last week and so far no one has responded, so I thought I would bring this back here just in case someone else has encountered this problem.  I am kinda lost as to what to do here.

---

### Post by khelben1979 on 2009-09-15
Edit the /etc/X11/xorg.conf file with a text editor ([emacs]("http://en.wikipedia.org/wiki/Emacs") works good) and insert a # before the line where glx is noted. That should do it.

---

### Post by psyke83 on 2009-09-15
> **Diggs808 said:**
> I installed the latest updates today, then rebooted.  Now I can only get to the CLI.  When I try 'startx' I get a message that says that it failed to load module "glx" (loader failed, 7).  



This comes from my Xorg.0.log


This is from /var/log/Xorg.0.log
 (II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: _nv000028gl
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)


I filed a LP bug last week and so far no one has responded, so I thought I would bring this back here just in case someone else has encountered this problem.  I am kinda lost as to what to do here.

Just a suggestion: make your thread titles more relevant to the topic you're writing about. This is being discussed in probably half-a-dozen threads already.

For example:
[http://ubuntuforums.org/showthread.php?t=1267255](http://ubuntuforums.org/showthread.php?t=1267255)
[http://ubuntuforums.org/showthread.php?t=1244488](http://ubuntuforums.org/showthread.php?t=1244488)
[http://ubuntuforums.org/showthread.php?t=1267032](http://ubuntuforums.org/showthread.php?t=1267032)

---

