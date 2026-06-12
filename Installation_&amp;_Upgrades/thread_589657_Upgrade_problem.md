---
title: "Upgrade problem"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by shafin on 2007-10-24
I got the following problem:
I'm on feisty 64 bit
 > 
The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.

Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.Here are the files

Main_update_self.log:
```
2007-10-24 18:04:39,987 INFO release-upgrader version '0.81' started
2007-10-24 18:04:40,381 DEBUG lsb-release: 'feisty'
2007-10-24 18:04:40,381 DEBUG _pythonSymlinkCheck run
2007-10-24 18:04:41,167 DEBUG checkViewDepends()
2007-10-24 18:04:42,451 DEBUG useNetwork: 'True' (selected by user)
2007-10-24 18:07:55,413 INFO runDistUpgrader() called, re-exec self
```Main_Pre_req.log
```
2007-10-24 18:07:55,558 INFO release-upgrader version '0.81' started
2007-10-24 18:07:55,916 DEBUG lsb-release: 'feisty'
2007-10-24 18:07:55,916 DEBUG _pythonSymlinkCheck run
2007-10-24 18:07:56,772 DEBUG checkViewDepends()
2007-10-24 18:07:56,772 DEBUG getRequiredBackports()
2007-10-24 18:08:53,849 ERROR IOError in cache.update(): 'Failed to fetch http://bd.archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/binary-amd64/Packages.gz Sub-process gzip returned an error code (1)
'. Retrying (currentRetry: 0)
2007-10-24 18:09:38,339 ERROR IOError in cache.update(): 'Failed to fetch http://bd.archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/binary-amd64/Packages.gz Sub-process gzip returned an error code (1)
'. Retrying (currentRetry: 1)
2007-10-24 18:10:20,991 ERROR IOError in cache.update(): 'Failed to fetch http://bd.archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/binary-amd64/Packages.gz Sub-process gzip returned an error code (1)
'. Retrying (currentRetry: 2)
2007-10-24 18:10:20,991 ERROR doUpdate() failed complettely
2007-10-24 18:10:25,270 DEBUG marking 'release-upgrader-apt' for install
2007-10-24 18:10:25,347 DEBUG marking 'release-upgrader-dpkg' for install
2007-10-24 18:39:24,077 DEBUG pre-requists item: '<pkgAcquire::ItemIterator object: Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 1974216 DestFile:'/tmp/tmpKy8g2z/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_amd64.udeb' DescURI: 'http://bd.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-dpkg/release-upgrader-dpkg_1.14.5ubuntu11.' 
2007-10-24 18:39:24,078 DEBUG pre-requists item: '<pkgAcquire::ItemIterator object: Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 1312844 DestFile:'/tmp/tmpKy8g2z/backports/release-upgrader-apt_0.6.46.4ubuntu10.3_amd64.udeb' DescURI: 'http://bd.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-apt/release-upgrader-apt_0.6.46.4ubuntu10' 
2007-10-24 18:39:24,079 DEBUG extracting udeb '/tmp/tmpKy8g2z/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_amd64.udeb' 
2007-10-24 18:39:24,667 DEBUG extracting udeb '/tmp/tmpKy8g2z/backports/release-upgrader-apt_0.6.46.4ubuntu10.3_amd64.udeb'
```Main.log
```
2007-10-24 19:02:57,324 INFO release-upgrader version '0.81' started
2007-10-24 19:02:57,661 DEBUG lsb-release: 'feisty'
2007-10-24 19:02:57,662 DEBUG _pythonSymlinkCheck run
2007-10-24 19:02:58,391 DEBUG checkViewDepends()
2007-10-24 19:02:59,621 DEBUG useNetwork: 'False' (selected by user)
2007-10-24 19:02:59,622 DEBUG getRequiredBackports()
2007-10-24 19:02:59,622 DEBUG Searching for pre-requists on CDROM
2007-10-24 19:02:59,623 DEBUG copying pre-req '/cdrom/dists/stable/main/dist-upgrader/binary-amd64/release-upgrader-apt_0.6.46.4ubuntu10.3_amd64.udeb' to '/tmp/tmp.sjsnos7940/backports'
2007-10-24 19:02:59,628 DEBUG copying pre-req '/cdrom/dists/stable/main/dist-upgrader/binary-amd64/release-upgrader-dpkg_1.14.5ubuntu11.2_amd64.udeb' to '/tmp/tmp.sjsnos7940/backports'
2007-10-24 19:02:59,636 DEBUG extracting udeb '/tmp/tmp.sjsnos7940/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_amd64.udeb' 

```Apt.log
```

Installing openoffice.org-core as dep of openoffice.org-draw
Installing libpoppler1 as dep of libpoppler1-glib
Installing samba-common as dep of smbclient
Installing mysql-common as dep of libmysqlclient15off
Installing app-install-data as dep of gnome-app-install
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnash as dep of mozilla-plugin-gnash
Installing gnash-common as dep of gnash
Installing linux-restricted-modules-2.6.20-16-generic as dep of linux-restricted-modules-generic
Installing linux-image-2.6.20-16-generic as dep of linux-restricted-modules-2.6.20-16-generic
Installing openoffice.org-common as dep of openoffice.org-style-human
Installing hal-info as dep of hal
Installing amarok as dep of amarok-xine
Installing wine as dep of wine-dev
Installing linux-headers-2.6.20-16-generic as dep of linux-headers-generic
Installing linux-headers-2.6.20-16 as dep of linux-headers-2.6.20-16-generic
Installing libmagic1 as dep of file
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
Installing libpcrecpp0 as dep of subtitleeditor
Starting
Starting 2
Investigating gnash-common
Package gnash-common has broken dep on libfreetype6
Investigating gimp
Package gimp has broken dep on gimp-data
  Considering gimp-data 2 as a solution to gimp 1
  Removing gimp rather than change gimp-data
Investigating gnash
Package gnash has broken dep on gnash-common
  Considering gnash-common 4 as a solution to gnash 1
  Holding Back gnash rather than change gnash-common
Investigating gimp-print
Package gimp-print has broken dep on gimp
  Considering gimp 1 as a solution to gimp-print 0
  Removing gimp-print rather than change gimp
Investigating mozilla-plugin-gnash
Package mozilla-plugin-gnash has broken dep on gnash
  Considering gnash 1 as a solution to mozilla-plugin-gnash 0
  Holding Back mozilla-plugin-gnash rather than change gnash
Investigating stardict-gtk
Package stardict-gtk has broken dep on stardict-common
  Considering stardict-common 1 as a solution to stardict-gtk 0
  Removing stardict-gtk rather than change stardict-common
Investigating beagle
Package beagle has broken dep on libfreetype6
Investigating totem
Package totem has broken dep on totem-gstreamer
Package totem has broken dep on totem-xine
  Or group remove for totem
Investigating totem-mozilla
Package totem-mozilla has broken dep on totem-xine
Package totem-mozilla has broken dep on totem-gstreamer
  Or group remove for totem-mozilla
 Try to Re-Instate gnash-common
 Try to Re-Instate gnash
 Try to Re-Instate mozilla-plugin-gnash
 Try to Re-Instate beagle
Done
Installing desktop-effects as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing compiz as dep of desktop-effects
Installing gimp as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing gimp-print as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing totem as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing totem-mozilla as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating gimp
Package gimp has broken dep on gimp-data
  Considering gimp-data 2 as a solution to gimp 1
    Reinst Failed early because of gimp-data
  Removing gimp rather than change gimp-data
Investigating gimp-print
Package gimp-print has broken dep on gimp
  Considering gimp 1 as a solution to gimp-print 0
  Removing gimp-print rather than change gimp
Investigating totem
Package totem has broken dep on totem-gstreamer
Package totem has broken dep on totem-xine
  Or group remove for totem
Investigating totem-mozilla
Package totem-mozilla has broken dep on totem-xine
Package totem-mozilla has broken dep on totem-gstreamer
  Or group remove for totem-mozilla
Done
ERROR:root:Unauthenticated packages found: 'compiz f-spot gaim gimp-data gnome-accessibility-themes gthumb libbeagle0 libpurple0 libsensors3 libwnck-common libwnck18 lm-sensors notification-daemon pidgin pidgin-data pidgin-libnotify pidgin-plugin-pack rhythmbox sound-juicer stardict-common subtitleeditor tomboy uck'
dpkg-deb: `/tmp/tmp.THwaXb7858/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_amd64.udeb' is not a debian format archive
bzip2: (stdin) is not a bzip2 file.

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format
bzip2: (stdin) is not a bzip2 file.

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format
bzip2: (stdin) is not a bzip2 file.

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format
bzip2: (stdin) is not a bzip2 file.

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format
bzip2: (stdin) is not a bzip2 file.

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format
bzip2: (stdin) is not a bzip2 file.

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format
dpkg-deb: `/tmp/tmp.fQWOJw8529/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_amd64.udeb' is not a debian format archive
dpkg-deb: `/tmp/tmp.GJhsf30289/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_amd64.udeb' is not a debian format archive
dpkg-deb: `/tmp/tmp.znOHE30315/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_amd64.udeb' is not a debian format archive

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format
dpkg-deb: `/tmp/tmp.aUlMFZ5110/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_amd64.udeb' is not a debian format archive

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format
dpkg-deb: `/tmp/tmp.WwwXRo7689/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_amd64.udeb' is not a debian format archive
dpkg-deb: `/tmp/tmp.KQSgAw7712/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_amd64.udeb' is not a debian format archive
dpkg-deb: `/tmp/tmp.HVtbPc7801/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_amd64.udeb' is not a debian format archive
dpkg-deb: `/tmp/tmp.sjsnos7940/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_amd64.udeb' is not a debian format archive
```

---

