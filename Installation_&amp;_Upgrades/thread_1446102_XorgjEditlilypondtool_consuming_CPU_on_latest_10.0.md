---
title: "Xorg/jEdit/lilypondtool consuming CPU on latest 10.04"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by Nick Payne on 2010-04-03
I use jEdit with lilypondtool plugin quite a lot for writing lilypond source code. When I first upgraded this machine to 10.04 beta 1, I didn't notice any slowdown in jEdit, but an update applied in the last couple of days via apt-get update/upgrade has caused the display update become very slow when when entering text into lilypond ly source files in jEdit - the text in the edit window doesn't keep up with my typing. However, there has been no update to either jEdit or lilypondtool, so it's an update to something else that has caused the problem.

The PC has an i7 quad core CPU and 6Gb RAM. System monitor shows that memory use is only 12% of the physical RAM, but top shows Xorg never dropping below 25% CPU while editing an ly file with jEdit, and CPU goes to 90% or more while entering text.

I'm running Ubuntu i386 with the PAE kernel, jEdit 4.3.1 and the latest lilypondtool from the jEdit plugin repository..

---

### Post by Nick Payne on 2010-04-04
Well, the problem seems to have been fixed by the latest 6.19 sun-java6-bin which just installed via Update Manager. Xorg no longer goes crazy when entering text.

---

