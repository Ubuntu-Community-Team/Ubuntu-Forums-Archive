---
title: "xorg and Intel"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by slakkie on 2008-10-31
All, normally I would wait a month or so before I upgrade my boxes, but yesterday I decided be wild and I upgraded my box... 

Well, I lost my X.. see [http://www.euronet.nl/users/wesleys/intel-bug/](http://www.euronet.nl/users/wesleys/intel-bug/) for logs and lspci output. I found a bug on launchpad which has a similar error (but on pipe B, where I have it on pipe A). It should be resolved by the package that I have installed: xserver-xorg-video-intel 2:2.4.1-ubuntu10 but apparently it didn't.. :( 

If someone had similar issues and knows howto resolve them, please come forward :)

---

### Post by hornetster on 2008-10-31
I was having craploads of probs with this as well (new motherboard with intel express G43). Running both SUSE 11 and Ubuntu 8.10 RC and could only use the VESA client. All is fixed with the 8.10 full release. I am now a happy man! Sorry, this may not help you a great deal... :(

---

### Post by slakkie on 2008-10-31
The plot thickens.. When I start Gnome I do not have these errors..

Login into gnome/logout, repeat process: works.
Same thing with KDE, my machines hangs, and is unresponsive (only ssh access still works)..

And I'm a KDE user, so it isn't a real workaround for me.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/256142](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/256142) Looks like there are users with the exact same problem..

---

### Post by slakkie on 2008-11-03
Installing KDE3 resolved the issue :)

-edit-

It didn't, still get the underrun errors, but only after logging out..

---

