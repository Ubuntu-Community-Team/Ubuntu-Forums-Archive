---
title: "Upgrade to Edgy from Dapper - problems."
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by fidolip on 2007-03-27
Here's a message I get when I try to upgrade from Dapper to Edgy:

> 
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.


It comes up after the 'Modifying software channels'. Here is the main.log from /var/log/dist-upgrade/ (apt.log is way too long to paste it here, but if anyone feels that seeing it would help sloving my problem, then I can paste it somewhere else):

> 
2007-03-27 10:08:06,743 DEBUG Foreign: kadu
2007-03-27 10:08:06,744 DEBUG Obsolete: libdivxencore0-binary automatix2 realplay itouch-control fuse-utils libfuse2 ntfs-3g acroread-escript libdivx0-binary audacious-plugins skype hal-device-manager libntfs-3g0 libasyncns0 audacious-plugins-extra hal libhal1 glibc mozilla-acroread acroread totem-gstreamer-firefox-plugin makedev liba52-0.7.4 libdivxdecore0-binary libdvdcss2 ntfs-config audacious-plugins-dev audacious wengophone pmount computertemp libpulse0 libhal-storage1 audacious-dev w32codecs liboil0.3 gcc-4.1-base flash-plugin libflac6 easyubuntu
2007-03-27 10:08:06,745 DEBUG updateSourcesList()
2007-03-27 10:08:06,798 DEBUG rewriteSourcesList()
2007-03-27 10:08:07,177 DEBUG examining: 'deb-src [ftp://gb.archive.ubuntu.com/ubuntu/](ftp://gb.archive.ubuntu.com/ubuntu/) dapper main restricted'
2007-03-27 10:08:07,178 DEBUG entry 'deb-src [ftp://gb.archive.ubuntu.com/ubuntu/](ftp://gb.archive.ubuntu.com/ubuntu/) edgy main restricted' updated to new dist
2007-03-27 10:08:07,178 DEBUG examining: 'deb [ftp://gb.archive.ubuntu.com/ubuntu/](ftp://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted'
2007-03-27 10:08:07,178 DEBUG entry 'deb [ftp://gb.archive.ubuntu.com/ubuntu/](ftp://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted' updated to new dist
2007-03-27 10:08:07,178 DEBUG examining: 'deb-src [ftp://gb.archive.ubuntu.com/ubuntu/](ftp://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted'
2007-03-27 10:08:07,179 DEBUG entry 'deb-src [ftp://gb.archive.ubuntu.com/ubuntu/](ftp://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted' updated to new dist
2007-03-27 10:08:07,179 DEBUG examining: 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse'
2007-03-27 10:08:07,179 DEBUG entry 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main restricted multiverse' updated to new dist
2007-03-27 10:08:07,179 DEBUG examining: 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe'
2007-03-27 10:08:07,179 DEBUG entry 'deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe' updated to new dist
2007-03-27 10:08:07,180 DEBUG examining: 'deb [ftp://gb.archive.ubuntu.com/ubuntu/](ftp://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse'
2007-03-27 10:08:07,180 DEBUG entry 'deb [ftp://gb.archive.ubuntu.com/ubuntu/](ftp://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse' updated to new dist
2007-03-27 10:08:07,180 DEBUG examining: 'deb-src [ftp://gb.archive.ubuntu.com/ubuntu/](ftp://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse'
2007-03-27 10:08:07,180 DEBUG entry 'deb-src [ftp://gb.archive.ubuntu.com/ubuntu/](ftp://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse' updated to new dist
2007-03-27 10:08:07,180 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted'
2007-03-27 10:08:07,180 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted' updated to new dist
2007-03-27 10:08:07,181 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted'
2007-03-27 10:08:07,181 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted' updated to new dist
2007-03-27 10:08:07,181 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe'
2007-03-27 10:08:07,181 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe' updated to new dist
2007-03-27 10:08:07,181 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe'
2007-03-27 10:08:07,182 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe' updated to new dist
2007-03-27 10:08:07,182 DEBUG examining: 'deb [http://www.kadu.net/download/binary/ubuntu/repo](http://www.kadu.net/download/binary/ubuntu/repo) dapper main'
2007-03-27 10:08:07,183 DEBUG entry '# deb [http://www.kadu.net/download/binary/ubuntu/repo](http://www.kadu.net/download/binary/ubuntu/repo) dapper main' was disabled (unknown mirror)
2007-03-27 10:11:55,523 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'


Does anyone know how to fix it so that I can upgrade to Edgy?
Cheers,
fidolip

---

