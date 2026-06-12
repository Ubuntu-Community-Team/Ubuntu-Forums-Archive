---
title: "Problem Installing MS Fonts...?"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by LegendarySandwich on 2009-12-06
Hello, I am a very new user to Ubuntu. I tried to install Checkgmail, and this is what I got:

spencer@spencer-desktop:~$ sudo apt-get install checkgmail
[sudo] password for spencer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcrypt-blowfish-perl libcrypt-simple-perl libcrypt-ssleay-perl
  libemail-mime-encodings-perl libgtk2-sexy-perl libgtk2-trayicon-perl
  libmd5-perl libsexymm2 libxml-namespacesupport-perl libxml-sax-expat-perl
  libxml-sax-perl libxml-simple-perl
The following NEW packages will be installed:
  checkgmail libcrypt-blowfish-perl libcrypt-simple-perl libcrypt-ssleay-perl
  libemail-mime-encodings-perl libgtk2-sexy-perl libgtk2-trayicon-perl
  libmd5-perl libsexymm2 libxml-namespacesupport-perl libxml-sax-expat-perl
  libxml-sax-perl libxml-simple-perl
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 443kB of archives.
After this operation, 2,220kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libgtk2-trayicon-perl 0.06-1 [20.2kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libcrypt-ssleay-perl 0.57-1 [57.9kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libxml-namespacesupport-perl 1.09-3 [15.3kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libxml-sax-perl 0.96+dfsg-1 [84.6kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libxml-sax-expat-perl 0.40-1 [12.5kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libxml-simple-perl 2.18-2 [69.0kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libcrypt-blowfish-perl 2.10-1build2 [22.2kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libgtk2-sexy-perl 0.04-1 [36.5kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe checkgmail 1.13+svn43-0ubuntu1 [68.8kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libemail-mime-encodings-perl 1.313-1 [7,144B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libmd5-perl 2.03-1 [5,680B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libcrypt-simple-perl 0.06-5 [9,188B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libsexymm2 0.1.9-5 [34.0kB]
Fetched 443kB in 24s (17.8kB/s)                                                
Selecting previously deselected package libgtk2-trayicon-perl.
(Reading database ... 173426 files and directories currently installed.)
Unpacking libgtk2-trayicon-perl (from .../libgtk2-trayicon-perl_0.06-1_amd64.deb) ...
Selecting previously deselected package libcrypt-ssleay-perl.
Unpacking libcrypt-ssleay-perl (from .../libcrypt-ssleay-perl_0.57-1_amd64.deb) ...
Selecting previously deselected package libxml-namespacesupport-perl.
Unpacking libxml-namespacesupport-perl (from .../libxml-namespacesupport-perl_1.09-3_all.deb) ...
Selecting previously deselected package libxml-sax-perl.
Unpacking libxml-sax-perl (from .../libxml-sax-perl_0.96+dfsg-1_all.deb) ...
Selecting previously deselected package libxml-sax-expat-perl.
Unpacking libxml-sax-expat-perl (from .../libxml-sax-expat-perl_0.40-1_all.deb) ...
Selecting previously deselected package libxml-simple-perl.
Unpacking libxml-simple-perl (from .../libxml-simple-perl_2.18-2_all.deb) ...
Selecting previously deselected package libcrypt-blowfish-perl.
Unpacking libcrypt-blowfish-perl (from .../libcrypt-blowfish-perl_2.10-1build2_amd64.deb) ...
Selecting previously deselected package libgtk2-sexy-perl.
Unpacking libgtk2-sexy-perl (from .../libgtk2-sexy-perl_0.04-1_amd64.deb) ...
Selecting previously deselected package checkgmail.
Unpacking checkgmail (from .../checkgmail_1.13+svn43-0ubuntu1_all.deb) ...
Selecting previously deselected package libemail-mime-encodings-perl.
Unpacking libemail-mime-encodings-perl (from .../libemail-mime-encodings-perl_1.313-1_all.deb) ...
Selecting previously deselected package libmd5-perl.
Unpacking libmd5-perl (from .../libmd5-perl_2.03-1_all.deb) ...
Selecting previously deselected package libcrypt-simple-perl.
Unpacking libcrypt-simple-perl (from .../libcrypt-simple-perl_0.06-5_all.deb) ...
Selecting previously deselected package libsexymm2.
Unpacking libsexymm2 (from .../libsexymm2_0.1.9-5_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-12-06 14:31:49--  [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:31:59--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net) [following]
--2009-12-06 14:32:01--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:32:11--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2009-12-06 14:32:21--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving dfn.dl.sourceforge.net... 194.95.236.6
Connecting to dfn.dl.sourceforge.net|194.95.236.6|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net) [following]
--2009-12-06 14:32:23--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:32:33--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net) [following]
--2009-12-06 14:32:34--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:32:44--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2009-12-06 14:32:54--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net) [following]
--2009-12-06 14:32:56--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:33:06--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving ufpr.dl.sourceforge.net... 200.17.202.1, 200.236.31.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net) [following]
--2009-12-06 14:33:07--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net)
Resolving downloads.sourceforge.net... /failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:33:17--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net) [following]
--2009-12-06 14:33:18--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:33:28--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving voxel.dl.sourceforge.net... 208.122.62.226
Connecting to voxel.dl.sourceforge.net|208.122.62.226|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net) [following]
--2009-12-06 14:33:29--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:33:39--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2009-12-06 14:33:49--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving internap.dl.sourceforge.net... 64.7.222.131
Connecting to internap.dl.sourceforge.net|64.7.222.131|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net) [following]
--2009-12-06 14:33:51--  [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe]("http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe") [following]
--2009-12-06 14:33:52--  [http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving cdnetworks-us-2.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `cdnetworks-us-2.dl.sourceforge.net'
sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libgtk2-trayicon-perl (0.06-1) ...
Setting up libcrypt-ssleay-perl (0.57-1) ...
Setting up libxml-namespacesupport-perl (1.09-3) ...
Setting up libxml-sax-perl (0.96+dfsg-1) ...
update-perl-sax-parsers: Registering Perl SAX parser XML::SAX::PurePerl with priority 10...
update-perl-sax-parsers: Updating overall Perl SAX parser modules info file...

Creating config file /etc/perl/XML/SAX/ParserDetails.ini with new version

Setting up libxml-sax-expat-perl (0.40-1) ...
update-perl-sax-parsers: Registering Perl SAX parser XML::SAX::Expat with priority 50...
update-perl-sax-parsers: Updating overall Perl SAX parser modules info file...
Replacing config file /etc/perl/XML/SAX/ParserDetails.ini with new version

Setting up libxml-simple-perl (2.18-2) ...
Setting up libcrypt-blowfish-perl (2.10-1build2) ...
Setting up libgtk2-sexy-perl (0.04-1) ...
Setting up checkgmail (1.13+svn43-0ubuntu1) ...

Setting up libemail-mime-encodings-perl (1.313-1) ...
Setting up libmd5-perl (2.03-1) ...
Setting up libcrypt-simple-perl (0.06-5) ...
Setting up libsexymm2 (0.1.9-5) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
spencer@spencer-desktop:~$ sudo apt-get install ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ttf-mscorefonts-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-12-06 14:34:34--  [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:34:44--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net) [following]
--2009-12-06 14:34:46--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=switch.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:34:56--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2009-12-06 14:35:06--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving dfn.dl.sourceforge.net... 194.95.236.6
Connecting to dfn.dl.sourceforge.net|194.95.236.6|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net) [following]
--2009-12-06 14:35:07--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=dfn.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:35:17--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net) [following]
--2009-12-06 14:35:18--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=heanet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:35:28--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2009-12-06 14:35:38--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net) [following]
--2009-12-06 14:35:40--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=nchc.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:35:50--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving ufpr.dl.sourceforge.net... 200.17.202.1, 200.236.31.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net) [following]
--2009-12-06 14:35:51--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=ufpr.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:36:01--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net) [following]
--2009-12-06 14:36:02--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=internode.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:36:12--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving voxel.dl.sourceforge.net... 208.122.62.226
Connecting to voxel.dl.sourceforge.net|208.122.62.226|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net) [following]
--2009-12-06 14:36:13--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=voxel.dl.sourceforge.net)
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:36:23--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2009-12-06 14:36:33--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving internap.dl.sourceforge.net... 64.7.222.131
Connecting to internap.dl.sourceforge.net|64.7.222.131|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net) [following]
--2009-12-06 14:36:34--  [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=internap.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2009-12-06 14:36:35--  [http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://voxel.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving voxel.dl.sourceforge.net... 208.122.62.226
Connecting to voxel.dl.sourceforge.net|208.122.62.226|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198384 (194K) [application/octet-stream]
Saving to: `./andale32.exe'

100%[======================================>] 198,384      125K/s   in 1.6s    

2009-12-06 14:36:37 (125 KB/s) - `./andale32.exe' saved [198384/198384]

--2009-12-06 14:36:37--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe)
Resolving internap.dl.sourceforge.net... 64.7.222.131
Connecting to internap.dl.sourceforge.net|64.7.222.131|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=internap.dl.sourceforge.net) [following]
--2009-12-06 14:36:38--  [http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=internap.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=internap.dl.sourceforge.net)
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe) [following]
--2009-12-06 14:36:39--  [http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe)
Resolving cdnetworks-us-2.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `cdnetworks-us-2.dl.sourceforge.net'
andale32.exe: OK
andale32.exe: library not compiled to support large files.
Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
sha256sum: arialb32.exe: No such file or directory
arialb32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for arialb32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
spencer@spencer-desktop:~$ 

I think the problem is with installing ttf-mscorefonts-installer; I'm not sure, like I said I'm very new to Ubuntu (this is my second day of using it). Any other thing I tried to install also had this problem...help please?

---

### Post by darkod on 2009-12-06
It seems the source location is unavailable, either temporary or permanently. In the middle of the messages it says something about not being provided by MS any more, that may mean they were forced to take the source down. But it's strange that change not to be reflected in where the installer is looking for them.
I guess it's too much work to find and install the fonts one by one.

---

### Post by LegendarySandwich on 2009-12-06
So what do I do for the software that needs the fonts?

---

### Post by wojox on 2009-12-06
Install:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by 73ckn797 on 2009-12-06
> **wojox said:**
> Install:

```
sudo apt-get install ubuntu-restricted-extras
```


+1 this will do the trick.

---

### Post by LegendarySandwich on 2009-12-06
Thanks for the help, I will see if that does the trick :popcorn:

---

### Post by coffeecat on 2009-12-06
This is not the sourceforge server being down. This is a bug that affects some people (but not all):

[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

> **LegendarySandwich said:**
> So what do I do for the software that needs the fonts?

Some in that Launchpad thread are saying that the fix posted in post #21 works. If you don't want to do that, do you have the ttf files for the MS fonts you want installed? If so, create a hidden folder called '.fonts' in your home directory. Then, simply copy the ttf files to /home/yourusername/.fonts and the fonts will be available. This only works for your user account. If you want fonts installed so that all accounts can access them, post back and I'll post how to do that.

---

### Post by coffeecat on 2009-12-06
> **wojox said:**
> Install:

```
sudo apt-get install ubuntu-restricted-extras
```

I doubt that will work, unfortunately. Ubuntu-restricted-extras simply drags in the package ttf-mscorefonts-installer as a dependency and the OP has already identified this as the problem. They will run up against the same bug that I've linked to.

---

### Post by LegendarySandwich on 2009-12-06
I will try the fix posted in #21, but I'm a little scared since I think I will mess something up.

(And yeah, Coffeecat is right, it didn't work, but thanks anyways Wojox).

---

### Post by LegendarySandwich on 2009-12-06
I couldn't find the file /var/lib/dpkg/info/ttf-mscorefonts-installer.postinst. What now?

---

### Post by coffeecat on 2009-12-06
> **LegendarySandwich said:**
> I couldn't find the file /var/lib/dpkg/info/ttf-mscorefonts-installer.postinst. What now?

My other suggestion of copying the ttf files into /home/yourusername/.fonts . You say you are a new user of Ubuntu. Does that mean you have been using Windows? If so, just look in C:\Windows\Fonts. All the core font ttf files you need are there.

---

### Post by LegendarySandwich on 2009-12-06
> **coffeecat said:**
> My other suggestion of copying the ttf files into /home/yourusername/.fonts . You say you are a new user of Ubuntu. Does that mean you have been using Windows? If so, just look in C:\Windows\Fonts. All the core font ttf files you need are there.
Oh, forgot about your other suggestion. And yes, I have been using Windows XP. 

I'm going to try to copy the files now.

---

### Post by coffeecat on 2009-12-06
Good luck! I'm logging off now - late here. But I'll check this thread tomorrow in case you need to post again.

---

### Post by LegendarySandwich on 2009-12-06
Since there wasn't a .fonts folder there, I made one and copied all the .tff files into it, but when I try to install an application via the Terminal it still tries to download the MS Fonts.

Did I miss a step or do anything wrong?

---

### Post by wojox on 2009-12-06
Interesting ubuntu-restricted-extras worked for me.

Get rid of the installer:

```
sudo apt-get --purge remove ttf-mscorefonts-installer
```

---

### Post by LegendarySandwich on 2009-12-06
Wow, thanks, I think that did it!

:KS

If it didn't I will post here again.

---

### Post by wojox on 2009-12-06
If not try the .deb file here: [http://packages.ubuntu.com/karmic/all/ttf-mscorefonts-installer/download](http://packages.ubuntu.com/karmic/all/ttf-mscorefonts-installer/download)

---

### Post by LegendarySandwich on 2009-12-06
> **wojox said:**
> If not try the .deb file here: [http://packages.ubuntu.com/karmic/all/ttf-mscorefonts-installer/download](http://packages.ubuntu.com/karmic/all/ttf-mscorefonts-installer/download)
Okay, if the problem persists I will try that link.

Thanks again!

---

### Post by presence1960 on 2009-12-06
That is really annoying pasting all that text without putting Code tags around it. next time you paste a good deal of text on here please highlight all text after it is pasted and click # in the toolbar at the top please. Like this:

```
spencer@spencer-desktop:~$ sudo apt-get install checkgmail
[sudo] password for spencer:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
libcrypt-blowfish-perl libcrypt-simple-perl libcrypt-ssleay-perl
libemail-mime-encodings-perl libgtk2-sexy-perl libgtk2-trayicon-perl
libmd5-perl libsexymm2 libxml-namespacesupport-perl libxml-sax-expat-perl
libxml-sax-perl libxml-simple-perl
The following NEW packages will be installed:
checkgmail libcrypt-blowfish-perl libcrypt-simple-perl libcrypt-ssleay-perl
libemail-mime-encodings-perl libgtk2-sexy-perl libgtk2-trayicon-perl
libmd5-perl libsexymm2 libxml-namespacesupport-perl libxml-sax-expat-perl
libxml-sax-perl libxml-simple-perl
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 443kB of archives.
After this operation, 2,220kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic/universe libgtk2-trayicon-perl 0.06-1 [20.2kB]
Get:2 http://us.archive.ubuntu.com karmic/universe libcrypt-ssleay-perl 0.57-1 [57.9kB]
Get:3 http://us.archive.ubuntu.com karmic/main libxml-namespacesupport-perl 1.09-3 [15.3kB]
Get:4 http://us.archive.ubuntu.com karmic/main libxml-sax-perl 0.96+dfsg-1 [84.6kB]
Get:5 http://us.archive.ubuntu.com karmic/main libxml-sax-expat-perl 0.40-1 [12.5kB]
Get:6 http://us.archive.ubuntu.com karmic/main libxml-simple-perl 2.18-2 [69.0kB]
Get:7 http://us.archive.ubuntu.com karmic/main libcrypt-blowfish-perl 2.10-1build2 [22.2kB]
Get:8 http://us.archive.ubuntu.com karmic/universe libgtk2-sexy-perl 0.04-1 [36.5kB]
Get:9 http://us.archive.ubuntu.com karmic/universe checkgmail 1.13+svn43-0ubuntu1 [68.8kB]
Get:10 http://us.archive.ubuntu.com karmic/universe libemail-mime-encodings-perl 1.313-1 [7,144B]
Get:11 http://us.archive.ubuntu.com karmic/universe libmd5-perl 2.03-1 [5,680B]
Get:12 http://us.archive.ubuntu.com karmic/universe libcrypt-simple-perl 0.06-5 [9,188B]
Get:13 http://us.archive.ubuntu.com karmic/universe libsexymm2 0.1.9-5 [34.0kB]
Fetched 443kB in 24s (17.8kB/s)
Selecting previously deselected package libgtk2-trayicon-perl.
(Reading database ... 173426 files and directories currently installed.)
Unpacking libgtk2-trayicon-perl (from .../libgtk2-trayicon-perl_0.06-1_amd64.deb) ...
Selecting previously deselected package libcrypt-ssleay-perl.
Unpacking libcrypt-ssleay-perl (from .../libcrypt-ssleay-perl_0.57-1_amd64.deb) ...
Selecting previously deselected package libxml-namespacesupport-perl.
Unpacking libxml-namespacesupport-perl (from .../libxml-namespacesupport-perl_1.09-3_all.deb) ...
Selecting previously deselected package libxml-sax-perl.
Unpacking libxml-sax-perl (from .../libxml-sax-perl_0.96+dfsg-1_all.deb) ...
Selecting previously deselected package libxml-sax-expat-perl.
Unpacking libxml-sax-expat-perl (from .../libxml-sax-expat-perl_0.40-1_all.deb) ...
Selecting previously deselected package libxml-simple-perl.
Unpacking libxml-simple-perl (from .../libxml-simple-perl_2.18-2_all.deb) ...
Selecting previously deselected package libcrypt-blowfish-perl.
Unpacking libcrypt-blowfish-perl (from .../libcrypt-blowfish-perl_2.10-1build2_amd64.deb) ...
Selecting previously deselected package libgtk2-sexy-perl.
Unpacking libgtk2-sexy-perl (from .../libgtk2-sexy-perl_0.04-1_amd64.deb) ...
Selecting previously deselected package checkgmail.
Unpacking checkgmail (from .../checkgmail_1.13+svn43-0ubuntu1_all.deb) ...
Selecting previously deselected package libemail-mime-encodings-perl.
Unpacking libemail-mime-encodings-perl (from .../libemail-mime-encodings-perl_1.313-1_all.deb) ...
Selecting previously deselected package libmd5-perl.
Unpacking libmd5-perl (from .../libmd5-perl_2.03-1_all.deb) ...
Selecting previously deselected package libcrypt-simple-perl.
Unpacking libcrypt-simple-perl (from .../libcrypt-simple-perl_0.06-5_all.deb) ...
Selecting previously deselected package libsexymm2.
Unpacking libsexymm2 (from .../libsexymm2_0.1.9-5_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility". This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-12-06 14:31:49-- http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:31:59-- http://switch.dl.sourceforge.net/sou...s/andale32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sou...ourceforge.net [following]
--2009-12-06 14:32:01-- http://downloads.sourceforge.net/sou...ourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:32:11-- http://mesh.dl.sourceforge.net/sourc...s/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2009-12-06 14:32:21-- http://dfn.dl.sourceforge.net/source...s/andale32.exe
Resolving dfn.dl.sourceforge.net... 194.95.236.6
Connecting to dfn.dl.sourceforge.net|194.95.236.6|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sou...ourceforge.net [following]
--2009-12-06 14:32:23-- http://downloads.sourceforge.net/sou...ourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:32:33-- http://heanet.dl.sourceforge.net/sou...s/andale32.exe
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sou...ourceforge.net [following]
--2009-12-06 14:32:34-- http://downloads.sourceforge.net/sou...ourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:32:44-- http://jaist.dl.sourceforge.net/sour...s/andale32.exe
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2009-12-06 14:32:54-- http://nchc.dl.sourceforge.net/sourc...s/andale32.exe
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sou...ourceforge.net [following]
--2009-12-06 14:32:56-- http://downloads.sourceforge.net/sou...ourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:33:06-- http://ufpr.dl.sourceforge.net/sourc...s/andale32.exe
Resolving ufpr.dl.sourceforge.net... 200.17.202.1, 200.236.31.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sou...ourceforge.net [following]
--2009-12-06 14:33:07-- http://downloads.sourceforge.net/sou...ourceforge.net
Resolving downloads.sourceforge.net... /failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:33:17-- http://internode.dl.sourceforge.net/...s/andale32.exe
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sou...ourceforge.net [following]
--2009-12-06 14:33:18-- http://downloads.sourceforge.net/sou...ourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:33:28-- http://voxel.dl.sourceforge.net/sour...s/andale32.exe
Resolving voxel.dl.sourceforge.net... 208.122.62.226
Connecting to voxel.dl.sourceforge.net|208.122.62.226|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sou...ourceforge.net [following]
--2009-12-06 14:33:29-- http://downloads.sourceforge.net/sou...ourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:33:39-- http://kent.dl.sourceforge.net/sourc...s/andale32.exe
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2009-12-06 14:33:49-- http://internap.dl.sourceforge.net/s...s/andale32.exe
Resolving internap.dl.sourceforge.net... 64.7.222.131
Connecting to internap.dl.sourceforge.net|64.7.222.131|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://prdownloads.sourceforge.net/c...ourceforge.net [following]
--2009-12-06 14:33:51-- http://prdownloads.sourceforge.net/c...ourceforge.net
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://cdnetworks-us-2.dl.sourceforg...l/andale32.exe [following]
--2009-12-06 14:33:52-- http://cdnetworks-us-2.dl.sourceforg...l/andale32.exe
Resolving cdnetworks-us-2.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `cdnetworks-us-2.dl.sourceforge.net'
sha256sum: andale32.exe: No such file or directory
andale32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for andale32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
subprocess installed post-installation script returned error exit status 1
Setting up libgtk2-trayicon-perl (0.06-1) ...
Setting up libcrypt-ssleay-perl (0.57-1) ...
Setting up libxml-namespacesupport-perl (1.09-3) ...
Setting up libxml-sax-perl (0.96+dfsg-1) ...
update-perl-sax-parsers: Registering Perl SAX parser XML::SAX:urePerl with priority 10...
update-perl-sax-parsers: Updating overall Perl SAX parser modules info file...

Creating config file /etc/perl/XML/SAX/ParserDetails.ini with new version

Setting up libxml-sax-expat-perl (0.40-1) ...
update-perl-sax-parsers: Registering Perl SAX parser XML::SAX::Expat with priority 50...
update-perl-sax-parsers: Updating overall Perl SAX parser modules info file...
Replacing config file /etc/perl/XML/SAX/ParserDetails.ini with new version

Setting up libxml-simple-perl (2.18-2) ...
Setting up libcrypt-blowfish-perl (2.10-1build2) ...
Setting up libgtk2-sexy-perl (0.04-1) ...
Setting up checkgmail (1.13+svn43-0ubuntu1) ...

Setting up libemail-mime-encodings-perl (1.313-1) ...
Setting up libmd5-perl (2.03-1) ...
Setting up libcrypt-simple-perl (0.06-5) ...
Setting up libsexymm2 (0.1.9-5) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
spencer@spencer-desktop:~$ sudo apt-get install ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree
Reading state information... Done
ttf-mscorefonts-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ttf-mscorefonts-installer (3.0) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility". This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-12-06 14:34:34-- http://downloads.sourceforge.net/corefonts/andale32.exe
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:34:44-- http://switch.dl.sourceforge.net/sou...s/andale32.exe
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sou...ourceforge.net [following]
--2009-12-06 14:34:46-- http://downloads.sourceforge.net/sou...ourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:34:56-- http://mesh.dl.sourceforge.net/sourc...s/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2009-12-06 14:35:06-- http://dfn.dl.sourceforge.net/source...s/andale32.exe
Resolving dfn.dl.sourceforge.net... 194.95.236.6
Connecting to dfn.dl.sourceforge.net|194.95.236.6|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sou...ourceforge.net [following]
--2009-12-06 14:35:07-- http://downloads.sourceforge.net/sou...ourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:35:17-- http://heanet.dl.sourceforge.net/sou...s/andale32.exe
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sou...ourceforge.net [following]
--2009-12-06 14:35:18-- http://downloads.sourceforge.net/sou...ourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:35:28-- http://jaist.dl.sourceforge.net/sour...s/andale32.exe
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2009-12-06 14:35:38-- http://nchc.dl.sourceforge.net/sourc...s/andale32.exe
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sou...ourceforge.net [following]
--2009-12-06 14:35:40-- http://downloads.sourceforge.net/sou...ourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:35:50-- http://ufpr.dl.sourceforge.net/sourc...s/andale32.exe
Resolving ufpr.dl.sourceforge.net... 200.17.202.1, 200.236.31.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sou...ourceforge.net [following]
--2009-12-06 14:35:51-- http://downloads.sourceforge.net/sou...ourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:36:01-- http://internode.dl.sourceforge.net/...s/andale32.exe
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sou...ourceforge.net [following]
--2009-12-06 14:36:02-- http://downloads.sourceforge.net/sou...ourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:36:12-- http://voxel.dl.sourceforge.net/sour...s/andale32.exe
Resolving voxel.dl.sourceforge.net... 208.122.62.226
Connecting to voxel.dl.sourceforge.net|208.122.62.226|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://downloads.sourceforge.net/sou...ourceforge.net [following]
--2009-12-06 14:36:13-- http://downloads.sourceforge.net/sou...ourceforge.net
Resolving downloads.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `downloads.sourceforge.net'
--2009-12-06 14:36:23-- http://kent.dl.sourceforge.net/sourc...s/andale32.exe
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2009-12-06 14:36:33-- http://internap.dl.sourceforge.net/s...s/andale32.exe
Resolving internap.dl.sourceforge.net... 64.7.222.131
Connecting to internap.dl.sourceforge.net|64.7.222.131|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://prdownloads.sourceforge.net/c...ourceforge.net [following]
--2009-12-06 14:36:34-- http://prdownloads.sourceforge.net/c...ourceforge.net
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://voxel.dl.sourceforge.net/proj...l/andale32.exe [following]
--2009-12-06 14:36:35-- http://voxel.dl.sourceforge.net/proj...l/andale32.exe
Resolving voxel.dl.sourceforge.net... 208.122.62.226
Connecting to voxel.dl.sourceforge.net|208.122.62.226|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198384 (194K) [application/octet-stream]
Saving to: `./andale32.exe'

100%[======================================>] 198,384 125K/s in 1.6s

2009-12-06 14:36:37 (125 KB/s) - `./andale32.exe' saved [198384/198384]

--2009-12-06 14:36:37-- http://internap.dl.sourceforge.net/s...s/arialb32.exe
Resolving internap.dl.sourceforge.net... 64.7.222.131
Connecting to internap.dl.sourceforge.net|64.7.222.131|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://prdownloads.sourceforge.net/c...ourceforge.net [following]
--2009-12-06 14:36:38-- http://prdownloads.sourceforge.net/c...ourceforge.net
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://cdnetworks-us-2.dl.sourceforg...l/arialb32.exe [following]
--2009-12-06 14:36:39-- http://cdnetworks-us-2.dl.sourceforg...l/arialb32.exe
Resolving cdnetworks-us-2.dl.sourceforge.net... failed: Connection timed out.
wget: unable to resolve host address `cdnetworks-us-2.dl.sourceforge.net'
andale32.exe: OK
andale32.exe: library not compiled to support large files.
Extracting cabinet: andale32.exe
extracting fontinst.inf
extracting andale.inf
extracting fontinst.exe
extracting AndaleMo.TTF
extracting ADVPACK.DLL
extracting W95INF32.DLL
extracting W95INF16.DLL

All done, no errors.
sha256sum: arialb32.exe: No such file or directory
arialb32.exe: FAILED open or read
sha256sum: WARNING: 1 of 1 listed file could not be read
Checksum mismatch for arialb32.exe, aborting!
dpkg: error processing ttf-mscorefonts-installer (--configure):
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
spencer@spencer-desktop:~$ 
```

The community thanks you for your co-operation.

---

### Post by coffeecat on 2009-12-07
> **LegendarySandwich said:**
> Since there wasn't a .fonts folder there, I made one and copied all the .tff files into it, but when I try to install an application via the Terminal it still tries to download the MS Fonts.

Did I miss a step or do anything wrong?

Although wojox's solution stopped the system trying to download the mscorefonts again, if you try to install ubuntu-restricted-extras you'll run into the same problem again because u-r-e will mark the corefonts installer for installation again.

If you do want all the codec goodies (+flash +java) that u-r-e gives you, mark ubuntu-restricted-extras for installation in Synaptic but, before clicking on apply, go to ttf-mscorefonts-installer and unmark it. Now click on apply and, hopefully, the corefonts installer won't bother you again.

If you do decide to download the ttf-mscorefonts-installer_3.0_all.deb file, best of luck, but I fear it may not succeed. Your problem is probably the bug I linked to - it seems to be something to do with a failure of DNS resolution and timeouts although, frankly, I don't understand it. So, however you try to use the ttf-mscorefonts-installer, it will probably fail. Using ubuntu-restricted-extras to install the mscorefonts worked for both wojox and myself because we weren't hit by this weird bug. You were one of the unlucky ones.

By the way, did copying the .ttf files into ~/.fonts work for you?

---

### Post by LegendarySandwich on 2009-12-08
> **presence1960 said:**
> That is really annoying pasting all that text without putting Code tags around it. next time you paste a good deal of text on here please highlight all text after it is pasted and click # in the toolbar at the top please. Like this:

(code) The community thanks you for your co-operation.
Oh, sorry, next time I will put code tags around the code. Thanks.
> **coffeecat said:**
> Although wojox's solution stopped the system trying to download the mscorefonts again, if you try to install ubuntu-restricted-extras you'll run into the same problem again because u-r-e will mark the corefonts installer for installation again.

If you do want all the codec goodies (+flash +java) that u-r-e gives you, mark ubuntu-restricted-extras for installation in Synaptic but, before clicking on apply, go to ttf-mscorefonts-installer and unmark it. Now click on apply and, hopefully, the corefonts installer won't bother you again.

If you do decide to download the ttf-mscorefonts-installer_3.0_all.deb file, best of luck, but I fear it may not succeed. Your problem is probably the bug I linked to - it seems to be something to do with a failure of DNS resolution and timeouts although, frankly, I don't understand it. So, however you try to use the ttf-mscorefonts-installer, it will probably fail. Using ubuntu-restricted-extras to install the mscorefonts worked for both wojox and myself because we weren't hit by this weird bug. You were one of the unlucky ones.

By the way, did copying the .ttf files into ~/.fonts work for you?
Okay, next time I run the U-R-E I will uncheck those fonts.

And no, copying the fonts didn't work unfortunately.

---

### Post by efflandt on 2009-12-08
The problems I had with ttf-mscorefonts-installer on one system was apparently related to the DNS timeout issue mentioned, as a result of my mistake.  When I manually added nameservers for networking, I mistyped the IP of the first one as beginning 192 when it should have been 172.  So some things worked falling back to the 2nd nameserver, but ttf-mscorefonts-installer apparently timed out before it got that far.

At first I thought sourceforge.net or its DNS was down, but strangely I could access [http://sorceforge.net/](http://sorceforge.net/) with Firefox.  When I used the **host** command to lookup the sourceforge subdomains is when I noticed that I had the wrong IP for one of my nameservers.

---

### Post by coffeecat on 2009-12-09
> **LegendarySandwich said:**
> And no, copying the fonts didn't work unfortunately.

I have never, ever had a failure in the dozens of times I have copied ttf fonts into a hidden ~/.fonts folder. So, let's check a few things. Did you make the folder /home/*yourusername*/.fonts ? There's a dot at the beginning of '.fonts'. It must be all lower-case. Double-check there's not a typo. Are the .ttf files in the ~/.fonts folder? Sorry to ask such an obvious question, but I really cannot see many ways that this can go wrong. Lastly - although I don't think this matters - some of the files will be fontname.TTF rather than fontname.ttf. Try changing the extension to .ttf.

Also - when you say 'didn't work', what do you mean? What apps do you mean? Are the fonts inaccessible in all apps. Have a look in OpenOffice Writer. Are they there? Right-click on the desktop, choose 'Change Desktop Background' and then click on the Fonts tab. When you click on one of those fonts, are the fonts you put in ~/.fonts there? Open firefox > Edit > Preferences > Content tab. Drop down the Default font list. Are your fonts appearing there?

I can post the method for installing .ttf font files system-wide if you want, but I'm really puzzled when you say that putting them in ~/.fonts didn't work.

---

### Post by LegendarySandwich on 2009-12-09
> **coffeecat said:**
> I have never, ever had a failure in the dozens of times I have copied ttf fonts into a hidden ~/.fonts folder. So, let's check a few things. Did you make the folder /home/*yourusername*/.fonts ? There's a dot at the beginning of '.fonts'. It must be all lower-case. Double-check there's not a typo. Are the .ttf files in the ~/.fonts folder? Sorry to ask such an obvious question, but I really cannot see many ways that this can go wrong. Lastly - although I don't think this matters - some of the files will be fontname.TTF rather than fontname.ttf. Try changing the extension to .ttf.

Also - when you say 'didn't work', what do you mean? What apps do you mean? Are the fonts inaccessible in all apps. Have a look in OpenOffice Writer. Are they there? Right-click on the desktop, choose 'Change Desktop Background' and then click on the Fonts tab. When you click on one of those fonts, are the fonts you put in ~/.fonts there? Open firefox > Edit > Preferences > Content tab. Drop down the Default font list. Are your fonts appearing there?

I can post the method for installing .ttf font files system-wide if you want, but I'm really puzzled when you say that putting them in ~/.fonts didn't work.
Yes, right place and folder name. And yes, a lot of the extensions are .TFF instead of .tff.

When I said didn't work, I meant the installer would keep trying to install the fonts. I think all the fonts work in the applications.

Thanks for the help, but I think the problem's already been solved.

---

