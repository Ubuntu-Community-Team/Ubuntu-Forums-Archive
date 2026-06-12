---
title: "weird ghost in dpkg"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by querent on 2008-09-13
So I'm applying for a job with [fonality]("http://www.fonality.com/"), and was installing a [hudlite]("http://www.hudlite.org/") client on my mom's laptop (mine is [trixbox]("http://www.trixbox.org") now).  I got the client as an rpm file from [here]("http://www.hudlite.org/downloads.htm"), used alien to make it a .deb, and installed it.  Tried to run a setup script called start_HUD.sh, and it failed do to the lack of a 'java runtime environment'.  

My worry is that now dpkg does things like the following.  Any 'apt-get install' command has a tail like this:

```

...
Selecting previously deselected package gparted.
(Reading database ... 97254 files and directories currently installed.)
Unpacking gparted (from .../gparted_0.3.5-1ubuntu3_i386.deb) ...
Setting up hud-lite (1.1.1170-2) ...
chmod: cannot access `/hud-lite': No such file or directory
dpkg: error processing hud-lite (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gparted (0.3.5-1ubuntu3) ...

Errors were encountered while processing:
 hud-lite
E: Sub-process /usr/bin/dpkg returned an error code (1)
lynn@lynn-laptop:/usr/fonality/hud-lite$

```

WHY IS DPKG STILL TALKING ABOUT HUD-LITE?  It is creeping me out.

---

### Post by querent on 2008-09-13
hm...this may not be the proper place for this question.  i thought 'installation' was more general.  sorry bout that.

---

### Post by cariboo on 2008-09-13
Seeing as you asked here, don't start a new thread in another forum.

Have you tried the broken package filter in synaptic?

Start synaptic then got to Edit-->Fix Broken Packages

Jim

---

### Post by querent on 2008-09-13
Yeah, I didn't post anywhere else.

So, thanks, but didn't work.  Any more ideas?

---

### Post by querent on 2008-09-14
Hello?

I'd really appreciate any help here.  I don't want to leave something strange unresolved on my mom's computer, and would rather not have to run a full reinstall.

Any help is appreciated and thanked in advance.

---

### Post by querent on 2008-09-14
Reinstalled.  Still curious, though, if anyone has an explanation.  Problems are the best places to learn, but I didn't have the time.

---

