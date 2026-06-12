---
title: "mzscheme not installing correctly"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by fedorastyle on 2007-04-28
I cannot install mzscheme, though, I am now past needing it. The problem is, Synaptic Package Manager breaks trying to install it, upgrade it, unmark it or remove it. Here is the output:

[I][INDENT]Preconfiguring packages ...
(Reading database ... 111721 files and directories currently installed.)
Preparing to replace mzscheme 1:352-1 (using .../mzscheme_1%3a352-10ubuntu1_i386.deb) ...

Stopping web server: mzserver ... start-stop-daemon: stat /usr/lib/plt/bin/mzscheme: No such file or directory (No such file or directory)
failed
invoke-rc.d: initscript mzscheme, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...

Stopping web server: mzserver ... start-stop-daemon: stat /usr/lib/plt/bin/mzscheme: No such file or directory (No such file or directory)
failed
invoke-rc.d: initscript mzscheme, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/mzscheme_1%3a352-10ubuntu1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mzscheme_1%3a352-10ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/INDENT][/I]

Would it be possible if someone helped, I can't do anything in terms of installing or upgrading until this is fixed.

---

