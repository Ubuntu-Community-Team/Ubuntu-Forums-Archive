---
title: "Package Operation Failed - Install and Remove functions in Software Center"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by emopdx on 2009-12-08
Recently installed Ubuntu 9.10 Karmic Koala and, when installing or removing programs in the Software Center, I am getting "Package Operation Failed" after everything.  Installations get hung up at the 71-73% range, then revert to 50%, and then the "Package Operation Failed" window.  The programs seem to get installed anyway but I do not know if their functionality is being affected.

Here are the details when I installed Google Gadgets:
installArchives() failed: Selecting previously deselected package libggadget-1.0-0. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 172182 files and directories currently installed.) 
Unpacking libggadget-1.0-0 (from .../libggadget-1.0-0_0.10.5-0.2ubuntu2_i386.deb) ... 
Selecting previously deselected package google-gadgets-common. 
Unpacking google-gadgets-common (from .../google-gadgets-common_0.10.5-0.2ubuntu2_i386.deb) ... 
Selecting previously deselected package google-gadgets-gst. 
Unpacking google-gadgets-gst (from .../google-gadgets-gst_0.10.5-0.2ubuntu2_i386.deb) ... 
Selecting previously deselected package libggadget-qt-1.0-0. 
Unpacking libggadget-qt-1.0-0 (from .../libggadget-qt-1.0-0_0.10.5-0.2ubuntu2_i386.deb) ... 
Selecting previously deselected package google-gadgets-xul. 
Unpacking google-gadgets-xul (from .../google-gadgets-xul_0.10.5-0.2ubuntu2_i386.deb) ... 
Selecting previously deselected package google-gadgets-qt. 
Unpacking google-gadgets-qt (from .../google-gadgets-qt_0.10.5-0.2ubuntu2_i386.deb) ... 
Processing triggers for shared-mime-info ... 
Unknown media type in type 'all/all' 
 
Unknown media type in type 'all/allfiles' 
 
Unknown media type in type 'uri/mms' 
 
Unknown media type in type 'uri/mmst' 
 
Unknown media type in type 'uri/mmsu' 
 
Unknown media type in type 'uri/pnm' 
 
Unknown media type in type 'uri/rtspt' 
 
Unknown media type in type 'uri/rtspu' 
 
Unknown media type in type 'fonts/package' 
 
Unknown media type in type 'interface/x-winamp-skin' 
 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for man-db ... 
Setting up ttf-mscorefonts-installer (3.0) ... 
 
These fonts were provided by Microsoft "in the interest of cross- 
platform compatibility".  This is no longer the case, but they are 
still available from third parties. 
 
You are free to download these fonts and use them for your own use, 
but you may not redistribute them in modified form, including changes 
to the file name or packaging format. 
 
--2009-12-08 00:04:05--  [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe) 
Resolving downloads.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `downloads.sourceforge.net' 
--2009-12-08 00:04:15--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving switch.dl.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `switch.dl.sourceforge.net' 
--2009-12-08 00:04:25--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving mesh.dl.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `mesh.dl.sourceforge.net' 
--2009-12-08 00:04:35--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving dfn.dl.sourceforge.net... 194.95.236.6 
Connecting to dfn.dl.sourceforge.net|194.95.236.6|:80... connected. 
HTTP request sent, awaiting response... 302 Found 
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net) [following] 
--2009-12-08 00:04:41--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net) 
Resolving downloads.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `downloads.sourceforge.net' 
--2009-12-08 00:04:51--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142 
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected. 
HTTP request sent, awaiting response... 302 Found 
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net) [following] 
--2009-12-08 00:04:57--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net) 
Resolving downloads.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `downloads.sourceforge.net' 
--2009-12-08 00:05:07--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving jaist.dl.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `jaist.dl.sourceforge.net' 
--2009-12-08 00:05:17--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17 
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected. 
HTTP request sent, awaiting response... 302 Found 
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net) [following] 
--2009-12-08 00:05:22--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net) 
Resolving downloads.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `downloads.sourceforge.net' 
--2009-12-08 00:05:32--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving ufpr.dl.sourceforge.net... 200.236.31.1 
Connecting to ufpr.dl.sourceforge.net|200.236.31.1|:80... connected. 
HTTP request sent, awaiting response... 302 Found 
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net) [following] 
--2009-12-08 00:05:39--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net) 
Resolving downloads.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `downloads.sourceforge.net' 
--2009-12-08 00:05:49--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving internode.dl.sourceforge.net... 150.101.135.12 
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected. 
HTTP request sent, awaiting response... 302 Found 
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net) [following] 
--2009-12-08 00:05:55--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net) 
Resolving downloads.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `downloads.sourceforge.net' 
--2009-12-08 00:06:05--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving voxel.dl.sourceforge.net... 208.122.31.16 
Connecting to voxel.dl.sourceforge.net|208.122.31.16|:80... connected. 
HTTP request sent, awaiting response... 302 Found 
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net) [following] 
--2009-12-08 00:06:11--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net) 
Resolving downloads.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `downloads.sourceforge.net' 
--2009-12-08 00:06:21--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving kent.dl.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `kent.dl.sourceforge.net' 
--2009-12-08 00:06:31--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) 
Resolving internap.dl.sourceforge.net... 64.7.222.131 
Connecting to internap.dl.sourceforge.net|64.7.222.131|:80... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net) [following] 
--2009-12-08 00:06:36--  [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net) 
Resolving prdownloads.sourceforge.net... 216.34.181.59 
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected. 
HTTP request sent, awaiting response... 302 Found 
Location: [http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following] 
--2009-12-08 00:06:41--  [http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) 
Resolving voxel.dl.sourceforge.net... 208.122.31.16 
Connecting to voxel.dl.sourceforge.net|208.122.31.16|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 198384 (194K) [application/octet-stream] 
Saving to: `./andale32.exe' 
 
  0% [                                       ] 0           --.-K/s                2% [                                       ] 5,054       19.8K/s                6% [=>                                     ] 13,142      25.7K/s               13% [====>                                  ] 26,622      34.7K/s               24% [========>                              ] 48,190      47.1K/s               41% [===============>                       ] 81,890      63.8K/s               65% [========================>              ] 130,418     83.3K/s               96% [====================================>  ] 192,426      108K/s               100%[======================================>] 198,384      109K/s   in 1.8s     
 
2009-12-08 00:06:49 (109 KB/s) - `./andale32.exe' saved [198384/198384] 
 
--2009-12-08 00:06:49--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe) 
Resolving internap.dl.sourceforge.net... 64.7.222.131 
Connecting to internap.dl.sourceforge.net|64.7.222.131|:80... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: [http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=internap.dl.sourceforge.net) [following] 
--2009-12-08 00:06:54--  [http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=internap.dl.sourceforge.net) 
Resolving prdownloads.sourceforge.net... 216.34.181.59 
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected. 
HTTP request sent, awaiting response... 302 Found 
Location: [http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe) [following] 
--2009-12-08 00:07:00--  [http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe) 
Resolving voxel.dl.sourceforge.net... 208.122.31.16 
Connecting to voxel.dl.sourceforge.net|208.122.31.16|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 168176 (164K) [application/octet-stream] 
Saving to: `./arialb32.exe' 
 
  0% [                                       ] 0           --.-K/s                3% [>                                      ] 5,056       18.3K/s                7% [==>                                    ] 13,144      25.2K/s               15% [=====>                                 ] 26,624      34.2K/s               28% [==========>                            ] 48,192      46.6K/s               48% [=================>                     ] 81,892      63.5K/s               83% [===============================>       ] 139,856     90.4K/s               100%[======================================>] 168,176      105K/s   in 1.6s     
 
2009-12-08 00:07:07 (105 KB/s) - `./arialb32.exe' saved [168176/168176] 
 
--2009-12-08 00:07:07--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/arial32.exe) 
Resolving internap.dl.sourceforge.net... 64.7.222.131 
Connecting to internap.dl.sourceforge.net|64.7.222.131|:80... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: [http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=internap.dl.sourceforge.net) [following] 
--2009-12-08 00:07:13--  [http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=internap.dl.sourceforge.net) 
Resolving prdownloads.sourceforge.net... 216.34.181.59 
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected. 
HTTP request sent, awaiting response... 302 Found 
Location: [http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe) [following] 
--2009-12-08 00:07:19--  [http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe) 
Resolving cdnetworks-us-2.dl.sourceforge.net... failed: Connection timed out. 
wget: unable to resolve host address `cdnetworks-us-2.dl.sourceforge.net' 
andale32.exe: OK 
Extracting cabinet: andale32.exe 
  extracting fontinst.inf 
  extracting andale.inf 
  extracting fontinst.exe 
  extracting AndaleMo.TTF 
  extracting ADVPACK.DLL 
  extracting W95INF32.DLL 
  extracting W95INF16.DLL 
 
All done, no errors. 
arialb32.exe: OK 
Extracting cabinet: arialb32.exe 
  extracting fontinst.exe 
  extracting fontinst.inf 
  extracting AriBlk.TTF 
 
All done, no errors. 
sha256sum: arial32.exe: No such file or directory 
arial32.exe: FAILED open or read 
sha256sum: WARNING: 1 of 1 listed file could not be read 
Checksum mismatch for arial32.exe, aborting! 
dpkg: error processing ttf-mscorefonts-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up libggadget-1.0-0 (0.10.5-0.2ubuntu2) ... 
 
Setting up google-gadgets-common (0.10.5-0.2ubuntu2) ... 
 
Setting up google-gadgets-gst (0.10.5-0.2ubuntu2) ... 
Setting up libggadget-qt-1.0-0 (0.10.5-0.2ubuntu2) ... 
 
Setting up google-gadgets-xul (0.10.5-0.2ubuntu2) ... 
Setting up google-gadgets-qt (0.10.5-0.2ubuntu2) ... 
 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 ttf-mscorefonts-installer

---

### Post by emopdx on 2009-12-08
Never mind.  It was that pesky ttf-mscorefonts-installer.  Got it fixed up.

---

### Post by gibsonsimswilson on 2009-12-08
Hi

I have just installed 9.10 and I have this error;

E: ttf-mscorefonts-installer: subprocess installed post-installation script returned error exit status 1

How did you fix it ?

Thanks

---

### Post by emopdx on 2009-12-14
To remove the installer, use this code in TERMINAL:

sudo apt-get remove ttf-mscorefonts-installer

If you want the fonts but not the installer, follow the directions on this site:
[http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/](http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/)

Good luck!

---

### Post by srijancb on 2011-03-11
I have got this error... How to repair?

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 184106 files and directories currently installed.) 
Unpacking libcupsys2 (from .../libcupsys2_1.2.2-0ubuntu0.6.06.20_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/libcupsys2_1.2.2-0ubuntu0.6.06.20_amd64.deb (--unpack): 
 trying to overwrite '/usr/lib/libcups.so.2', which is also in package libcups2 1.4.4-6ubuntu2.3 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/libcupsys2_1.2.2-0ubuntu0.6.06.20_amd64.deb 
dpkg: dependency problems prevent configuration of kdelibs4c2a: 
 kdelibs4c2a depends on libcupsys2 (>= 1.2.1); however: 
  Package libcupsys2 is not installed. 
dpkg: error processing kdelibs4c2a (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libktnef1: 
 libktnef1 depends on kdelibs4c2a (>= 4:3.5.2); however: 
  Package kdelibs4c2a is not configured yet. 
dpkg: error processing libktnef1 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libkcal2b: 
 libkcal2b depends on kdelibs4c2a (>= 4:3.5.2); however: 
  Package kdelibs4c2a is not configured yet. 
 libkcal2b depends on libktnef1 (>= 4:3.5.0); however: 
  Package libktnef1 is not configured yet. 
dpkg: error processing libkcal2b (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libkcddb1: 
 libkcddb1 depends on kdelibs4c2a (>= 4:3.5.2); however: 
  Package kdelibs4c2a is not configured yet. 
dpkg: error processing libkcddb1 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of kaddressbook: 
 kaddressbook depends on kdelibs4c2a (>= 4:3.5.2); however: 
  Package kdelibs4c2a is not configured yet. 
 kaddressbook depends on libkcal2b (>= 4:3.5.0); however: 
  Package libkcal2b is not configured yet. 
 kaddressbook depends on libktnef1 (>= 4:3.5.0); however: 
  Package libktnef1 is not configured yet. 
dpkg: error processing kaddressbook (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libkleopatra1: 
 libkleopatra1 depends on kdelibs4c2a (>= 4:3.5.2); however: 
  Package kdelibs4c2a is not configured yet. 
dpkg: error processing libkleopatra1 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of kdelibs-bin: 
 kdelibs-bin depends on kdelibs4c2a (>= 4:3.5.2); however: 
  Package kdelibs4c2a is not configured yet. 
 kdelibs-bin depends on libcupsys2 (>= 1.2.1); however: 
  Package libcupsys2 is not installed. 
dpkg: error processing kdelibs-bin (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of tellico: 
 tellico depends on kdelibs4c2a (>= 4:3.5.2); however: 
  Package kdelibs4c2a is not configured yet. 
 tellico depends on libkcal2b (>= 4:3.5.0); however: 
  Package libkcal2b is not configured yet. 
 tellico depends on libkcddb1 (>= 4:3.5.2); however: 
  Package libkcddb1 is not configured yet. 
 tellico depends on libktnef1 (>= 4:3.5.0); however: 
  Package libktnef1 is not configured yet. 
dpkg: error processing tellico (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libkdepim1a: 
 libkdepim1a depends on kdelibs4c2a (>= 4:3.5.2); however: 
  Package kdelibs4c2a is not configured yet. 
 libkdepim1a depends on libkcal2b (>= 4:3.5.0); however: 
  Package libkcal2b is not configured yet. 
dpkg: error processing libkdepim1a (--configure): 
 dependency problems - leaving unconfigured

---

