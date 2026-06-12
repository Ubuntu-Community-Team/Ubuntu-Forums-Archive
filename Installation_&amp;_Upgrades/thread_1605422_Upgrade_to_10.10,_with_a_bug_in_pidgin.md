---
title: "Upgrade to 10.10, with a bug in pidgin"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by jpmaglutac on 2010-10-25
So I upgraded to 10.10 earlier, but a strange bug has been appearing in my pidgin package. It says:
Preparing to replace pidgin 1:2.6.6-1ubuntu4 (using .../pidgin_1%3a2.7.3-1ubuntu3_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script (/var/lib/dpkg/info/pidgin.prerm): Exec format error
dpkg: warning: subprocess old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/pidgin_1%3a2.7.3-1ubuntu3_i386.deb (--unpack):
 there is no script in the new version of the package - giving up
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script (/var/lib/dpkg/info/pidgin.postinst): Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/pidgin_1%3a2.7.3-1ubuntu3_i386.deb
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on pidgin-data (<< 1:2.6.6-z); however:
  Version of pidgin-data on system is 1:2.7.3-1ubuntu3.
dpkg: error processing pidgin (--configure):
 dependency problems - leaving unconfigured

So it can't upgrade because it can't find a script to remove the program (I assume) so I tried removing from synaptics and even using dpkg -r --force-all pidgin and it says:

dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 221486 files and directories currently installed.)
Removing pidgin ...
dpkg (subprocess): unable to execute installed pre-removal script (/var/lib/dpkg/info/pidgin.prerm): Exec format error
dpkg: error processing pidgin (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script (/var/lib/dpkg/info/pidgin.postinst): Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 pidgin


So any way I can force remove this (maybe manually?) so that I can reinstall it? It's kind of bugging me everytime I open synaptics :confused:

---

