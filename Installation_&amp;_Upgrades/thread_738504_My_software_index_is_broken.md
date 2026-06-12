---
title: "My software index is broken"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by srkelley on 2008-03-28
EDIT: I forgot to add that a few weeks ago I upgraded from 7.04 to 7.10 and installed many programs, or at least selected them to be installed, but they completely filled the hard drive, it was impossible to delete anything. a poster here helped me out, but in the process it got rid of the ability to use the package manager. If those posts are needed I can bring them to you after I find them. 

When i try to run package manager I get this message:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

When I try to run the update manager I get this message:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

I've done what the system has told me to do, but after doing whatever it did it didn't solve the problem. I've tried a few fixes from other similar problems, but they have not worked.

I'm using Ubuntu 7.10. I have all of the privileges except for native super user privileges. I just type sudo before anything to get those type of privileges right?

Can anyone help me? I'm trying to install updates and get a few programs that I need for a school project.

Also, below is what i think is part of the problem or actual problem and it's been harder for me to search on it. The thingas I found for it havn't helped.



dpkg: dependency problems prevent configuration of tremulous:
 tremulous depends on tremulous-data (>= 1.1.0-1); however:
  Package tremulous-data is not installed.
dpkg: error processing tremulous (--configure):
 dependency problems - leaving unconfigured
Setting up libcommons-configuration-java (1.4-2) ...
Setting up libcommons-collections-java (2.1.1-6) ...



Below is everything that has come up in the terminal, but I think the above selection is what the problem is.

failedmirror=optusnet.dl.sourceforge.net
           => `./comic32.exe?download&failedmirror=optusnet.dl.sourceforge.net'
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=optusnet.dl.sourceforge.net](http://downloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=optusnet.dl.sourceforge.net) [following]
--17:41:51--  [http://downloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=optusnet.dl.sourceforge.net](http://downloads.sourceforge.net/corefonts/comic32.exe?download&failedmirror=optusnet.dl.sourceforge.net)
           => `./comic32.exe?download&failedmirror=optusnet.dl.sourceforge.net'
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://umn.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://umn.dl.sourceforge.net/sourceforge/corefonts/comic32.exe) [following]
--17:41:51--  [http://umn.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://umn.dl.sourceforge.net/sourceforge/corefonts/comic32.exe)
           => `./comic32.exe'
Resolving umn.dl.sourceforge.net... 128.101.240.209
Connecting to umn.dl.sourceforge.net|128.101.240.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246,008 (240K) [application/octet-stream]

100%[====================================>] 246,008      626.99K/s             

17:41:52 (625.65 KB/s) - `./comic32.exe' saved [246008/246008]

--17:41:52--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
           => `./courie32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--17:41:52--  [http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
           => `./courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--17:41:53--  [http://downloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
           => `./courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving downloads.sourceforge.net... 66.35.250.203
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://heanet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe) [following]
--17:41:53--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
           => `./courie32.exe'
Resolving heanet.dl.sourceforge.net... 193.1.193.66
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646,368 (631K) [application/octet-stream]

100%[====================================>] 646,368      436.47K/s             

17:41:55 (435.30 KB/s) - `./courie32.exe' saved [646368/646368]

--17:41:55--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
           => `./georgi32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--17:41:55--  [http://prdownloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
           => `./georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--17:41:56--  [http://downloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
           => `./georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving downloads.sourceforge.net... 66.35.250.203
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://heanet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe) [following]
--17:41:56--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
           => `./georgi32.exe'
Resolving heanet.dl.sourceforge.net... 193.1.193.66
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392,440 (383K) [application/octet-stream]

100%[====================================>] 392,440      297.08K/s             

17:41:57 (296.06 KB/s) - `./georgi32.exe' saved [392440/392440]

--17:41:58--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
           => `./impact32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--17:41:58--  [http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
           => `./impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--17:41:58--  [http://downloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
           => `./impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving downloads.sourceforge.net... 66.35.250.203
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://belnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe) [following]
--17:41:58--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
           => `./impact32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... failed: Connection timed out.
Giving up.

--17:42:04--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
           => `./impact32.exe'
Resolving internap.dl.sourceforge.net... 70.42.27.131
Connecting to internap.dl.sourceforge.net|70.42.27.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173,288 (169K) [application/octet-stream]

100%[====================================>] 173,288      560.58K/s             

17:42:04 (560.26 KB/s) - `./impact32.exe' saved [173288/173288]

--17:42:04--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
           => `./times32.exe'
Resolving internap.dl.sourceforge.net... 70.42.27.131
Connecting to internap.dl.sourceforge.net|70.42.27.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661,728 (646K) [application/octet-stream]

100%[====================================>] 661,728      959.10K/s             

17:42:05 (957.56 KB/s) - `./times32.exe' saved [661728/661728]

--17:42:05--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
           => `./trebuc32.exe'
Resolving internap.dl.sourceforge.net... 70.42.27.131
Connecting to internap.dl.sourceforge.net|70.42.27.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357,200 (349K) [application/octet-stream]

100%[====================================>] 357,200      755.04K/s             

17:42:06 (752.66 KB/s) - `./trebuc32.exe' saved [357200/357200]

--17:42:06--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
           => `./verdan32.exe'
Resolving internap.dl.sourceforge.net... 70.42.27.131
Connecting to internap.dl.sourceforge.net|70.42.27.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351,992 (344K) [application/octet-stream]

100%[====================================>] 351,992      658.62K/s             

17:42:07 (656.95 KB/s) - `./verdan32.exe' saved [351992/351992]

--17:42:07--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
           => `./webdin32.exe'
Resolving internap.dl.sourceforge.net... 70.42.27.131
Connecting to internap.dl.sourceforge.net|70.42.27.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185,072 (181K) [application/octet-stream]

100%[====================================>] 185,072      397.32K/s             

17:42:07 (396.44 KB/s) - `./webdin32.exe' saved [185072/185072]

Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Headline-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for Gulim-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
Couldn't get cwd: No such file or directory

Setting up libticalcs4 (4.6.1-2ubuntu1) ...

Setting up biblememorizer (0.5.2-1) ...
Setting up libgconf2-ruby (0.16.0-3ubuntu1) ...
Setting up kdegames-card-data (4:3.5.8-0ubuntu1) ...
Setting up libsdl-ttf2.0-0 (2.0.9-1) ...

Setting up wmgui (0.5.03+svn20070508-2) ...

Setting up gtimelog (0.0+svn65-1debian2) ...
Setting up libbcel-java (5.2-2ubuntu2) ...
dpkg: dependency problems prevent configuration of openarena:
 openarena depends on openarena-data (>= 0.7.0); however:
  Package openarena-data is not installed.
dpkg: error processing openarena (--configure):
 dependency problems - leaving unconfigured
Setting up libqt4-core (4.3.2-0ubuntu3.2) ...

Setting up kolourpaint (4:3.5.8-0ubuntu1) ...

Setting up libxalan110 (1.10-3.1) ...

dpkg: dependency problems prevent configuration of supertuxkart:
 supertuxkart depends on supertuxkart-data (>= 0.3-0ubuntu1); however:
  Package supertuxkart-data is not installed.
dpkg: error processing supertuxkart (--configure):
 dependency problems - leaving unconfigured
Setting up libsdl-console (1.3-4) ...

Setting up libglpng (1.45-4ubuntu1) ...

Setting up chromium-data (0.9.12-3) ...
Setting up freeciv-data (2.1.3-1~gutsy1) ...
Setting up libemail-valid-perl (0.179-1) ...
Setting up libopenobex1 (1.3-3ubuntu1) ...

Setting up libgdk-pixbuf2-ruby1.8 (0.16.0-3ubuntu1) ...
Setting up stardict-common (3.0.0-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up libcommons-logging-java (1.0.4-6ubuntu1) ...

Setting up samdump2 (1.1.0-1) ...
Setting up kicker (4:3.5.8-0ubuntu2.2) ...

Setting up libsdl-perl (1.20.3dfsg-2) ...
Setting up antlr (2.7.6-9ubuntu1) ...

Setting up libsdl-pango1 (0.1.2-1) ...

dpkg: dependency problems prevent configuration of tremulous:
 tremulous depends on tremulous-data (>= 1.1.0-1); however:
  Package tremulous-data is not installed.
dpkg: error processing tremulous (--configure):
 dependency problems - leaving unconfigured
Setting up libcommons-configuration-java (1.4-2) ...
Setting up libcommons-collections-java (2.1.1-6) ...

Setting up liblogkit-java (1.2.2-9) ...

Setting up klavaro (1.0.3-1ubuntu1) ...

Setting up kde-pwmanager (1.2.4-0ubuntu4) ...
No theme index file in '/usr/share/icons/locolor'.
If you really want to create an icon cache here, use --ignore-theme-index.

Setting up libjack0.100.0-0 (0.103.0-6ubuntu1) ...
Setting up planetpenguin-racer-data (0.3.1-10) ...
Setting up ladcca2 (0.4.0-6) ...

Setting up libcommons-lang-java (2.3-1) ...
Setting up libpango1-ruby1.8 (0.16.0-3ubuntu1) ...
Setting up libbtctl4 (0.9.0-0ubuntu1) ...

Setting up chromium (0.9.12-13ubuntu3) ...

Setting up email-reminder (0.5.7-1) ...

Setting up libqt4-gui (4.3.2-0ubuntu3.2) ...

Setting up kerry (1:0.2.1-0ubuntu3) ...

Setting up libwerken.xpath-java (0.9.4-9) ...
Setting up ophcrack (2.3.4~debian-1) ...

Setting up libgtk2-ruby1.8 (0.16.0-3ubuntu1) ...
Setting up stardict (3.0.0-1) ...

Setting up libfluidsynth1 (1.0.7a-1) ...

Setting up libgnomebt0 (0.9.1-0ubuntu1) ...

Setting up neverball (1.4.0-2ubuntu3) ...

Setting up stellarium (0.9.0-1) ...

Setting up freeciv-server (2.1.3-1~gutsy1) ...

Setting up anymeal (0.30-3) ...

Setting up rsibreak (0.8.0-4) ...

Setting up tilp (6.80-4ubuntu3) ...

Setting up korganizer (4:3.5.7enterprise20070926-0ubuntu2.1) ...

Setting up planetpenguin-racer (0.3.1-10) ...

Setting up kpat (4:3.5.8-0ubuntu1) ...

Setting up libglade2-ruby1.8 (0.16.0-3ubuntu1) ...
Setting up velocity (1.4-5) ...
Setting up python-qt4 (4.3-2ubuntu7.1) ...

Setting up scummvm (0.9.1-1build1) ...

Setting up freeciv-client-gtk (2.1.3-1~gutsy1) ...

Setting up gnome-phone-manager (0.10-0ubuntu1) ...
Setting up libglade2-ruby (0.16.0-3ubuntu1) ...
Setting up convertall (0.4.0-1) ...

Setting up gnome-splashscreen-manager (0.2-7ubuntu1) ...
Setting up lbreakout2-data (2.5.2-2.1ubuntu2) ...
Setting up lbreakout2 (2.5.2-2.1ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 nexuiz
 openarena
 supertuxkart
 tremulous
shirondale@shirondale-desktop:~$ sudo dpkg --clear-avail && sudo apt-get update
[sudo] password for shirondale:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US         
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                  
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Translation-en_US
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages
Fetched 7B in 2s (3B/s)  
Reading package lists... Done
shirondale@shirondale-desktop:~$

---

### Post by srkelley on 2008-03-28
Just wanted to post my six. I typed in

```
sudo synaptic manager
```

And manually picked out every broken file and had it completely removed. It was actually every file that was supposed to be installed a while back that got interrupted so I had to find 6 of them. It wasn't too much in the end.

---

