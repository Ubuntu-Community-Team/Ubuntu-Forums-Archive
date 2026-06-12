---
title: "java installation problem"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by gorlando on 2007-12-02
please help me as to why i am still getting these java error messages
when trying to start a game in pogo.com



sun java 6 packages are installed as stated in synaptic manager

using ubuntu 7.1


first error message

[http://game1.pogo.com/room/loading/jvmtest.jsp?ahst=game1.pogo.com&game=freebingo&anam=Temporary+Room+002&scrn=gorlando1820&rkey=freebingo-plfreebingosf431&site=pogo&rhst=www.pogo.com&rspt=6587](http://game1.pogo.com/room/loading/jvmtest.jsp?ahst=game1.pogo.com&game=freebingo&anam=Temporary+Room+002&scrn=gorlando1820&rkey=freebingo-plfreebingosf431&site=pogo&rhst=www.pogo.com&rspt=6587) wants to load an applet.
GNU Classpath's security implementation is not complete.
HOSTILE APPLETS WILL STEAL AND/OR DESTROY YOUR DATA!

i click on trust applet

then

game loading

The following error has occurred:
Java Not Found or Not Working

Explanation:
This error means Java (one of the technologies built into most browsers) is not working correctly on your browser.

You must have Java installed on your computer in order to run Pogo games, and it must be functioning properly. Either you don't have Java installed yet, or the Web browser you're currently using doesn't support Java or you have Java (or Javascript) disabled in your browser.

How to Fix the Problem:
Java is a free download that is required to play Pogo games. Not all computers come with Java pre-installed.

If you haven't played Pogo games before and are getting this error, you probably just need to install Java on your computer.
For instructions on installing Java for your operating system and browser click here.

If you believe Java might be installed but disabled for your browser, please be sure to enable the plugin for your browser. If you need help, click here.

If you already have Java installed and it is not disabled, your Java may be out-of-date or is no longer working. In that case, your Java might need to be upgraded or reinstalled. If you need help, click here.


java is activated in firefox


gary

---

### Post by rsambuca on 2007-12-02
You need the plugin installed as well.  Also, are you using 32 or 64bit Ubuntu?

---

### Post by gorlando on 2007-12-02
looks to me like the sun java plugin is already installed

i do not know which version of ubuntu.

---

### Post by rsambuca on 2007-12-03
Type the following command into a terminal and paste the output here.

uname -a

---

### Post by gorlando on 2007-12-03
Linux gary-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

---

### Post by jken146 on 2007-12-03
You can do ```
sudo apt-get install sun-java6-plugin
``` to confirm that the firefox Java plugin is actually installed.

---

### Post by rsambuca on 2007-12-03
OK, you have a 32 bit OS installed (the i686).  In your browser location bar, enter

about:plugins

See what java plugin is installed.

---

### Post by gorlando on 2007-12-03
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.


with reference to the other post, i really don't understand the info on about:plugins

---

### Post by rsambuca on 2007-12-03
OK, then open a terminal and enter

sudo apt-get install ubuntu-restricted-extras

---

### Post by gorlando on 2007-12-03
got all the extras.

still get error when trying to start the game.

when i go to Java.com, I now get
------------------
Congratulations!
 
You have the recommended Java installed (1.7.0).  
--------------------
when i do the verification.

That is the first time it has verified properly, but the game still gets the below error.

mozilla appears to have java enabled.

arghhhhhhhh!!!!!!!!
this should not be so difficult.


The following error has occurred:
Java Not Found or Not Working

Explanation:
This error means Java (one of the technologies built into most browsers) is not working correctly on your browser.

You must have Java installed on your computer in order to run Pogo games, and it must be functioning properly. Either you don't have Java installed yet, or the Web browser you're currently using doesn't support Java or you have Java (or Javascript) disabled in your browser.

How to Fix the Problem:
Java is a free download that is required to play Pogo games. Not all computers come with Java pre-installed.

If you haven't played Pogo games before and are getting this error, you probably just need to install Java on your computer.
For instructions on installing Java for your operating system and browser click here.

If you believe Java might be installed but disabled for your browser, please be sure to enable the plugin for your browser. If you need help, click here.

If you already have Java installed and it is not disabled, your Java may be out-of-date or is no longer working. In that case, your Java might need to be upgraded or reinstalled. If you need help, click here.

---

### Post by rsambuca on 2007-12-03
Type 

about:plugins

into the browser and paste everything in here.

---

### Post by gorlando on 2007-12-03
sorry, there must be a better way to paste...


Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.

________________________________________________________________________
Shockwave Flash
        File name: libflashplayer.so
        Shockwave Flash 9.0 r48
    MIME Type
   Description
     Suffixes
     Enabled
application/x-shockwave-flash
Shockwave Flash
swf
Yes
application/futuresplash
FutureSplash
Player
spl
Yes
GCJ Web Browser Plugin (using IcedTea) 1.4
        File name: gcjwebplugin.so
        The GCJ Web Browser Plugin (using IcedTea) executes Java
        applets.
    MIME Type
   Description
     Suffixes
     Enabled
application/x-java-vm
IcedTea
class,jar
Yes
application/x-java-applet
IcedTea
class,jar
Yes
application/x-java-applet;version=1.1
IcedTea
class,jar
Yes
application/x-java-applet;version=1.1.1
IcedTea
class,jar
Yes
application/x-java-applet;version=1.1.2
IcedTea
class,jar
Yes
application/x-java-applet;version=1.1.3
IcedTea
class,jar
Yes
application/x-java-applet;version=1.2
IcedTea
class,jar
Yes
application/x-java-applet;version=1.2.1
IcedTea
class,jar
Yes
application/x-java-applet;version=1.2.2
IcedTea
class,jar
Yes
application/x-java-applet;version=1.3
IcedTea
class,jar
Yes
application/x-java-applet;version=1.3.1
IcedTea
class,jar
Yes
application/x-java-applet;version=1.4
IcedTea
class,jar
Yes
application/x-java-applet;version=1.4.1
IcedTea
class,jar
Yes
application/x-java-applet;version=1.4.2
IcedTea
class,jar
Yes
application/x-java-applet;version=1.5
IcedTea
class,jar
Yes
application/x-java-applet;version=1.6
IcedTea
class,jar
Yes
application/x-java-applet;version=1.7
IcedTea
class,jar
Yes
application/x-java-applet;jpi-version=1.7.0_00
IcedTea
class,jar
Yes
application/x-java-bean
IcedTea
class,jar
Yes
application/x-java-bean;version=1.1
IcedTea
class,jar
Yes
application/x-java-bean;version=1.1.1
IcedTea
class,jar
Yes
application/x-java-bean;version=1.1.2
IcedTea
class,jar
Yes
application/x-java-bean;version=1.1.3
IcedTea
class,jar
Yes
application/x-java-bean;version=1.2
IcedTea
class,jar
Yes
application/x-java-bean;version=1.2.1
IcedTea
class,jar
Yes
application/x-java-bean;version=1.2.2
IcedTea
class,jar
Yes
application/x-java-bean;version=1.3
IcedTea
class,jar
Yes
application/x-java-bean;version=1.3.1
IcedTea
class,jar
Yes
application/x-java-bean;version=1.4
IcedTea
class,jar
Yes
application/x-java-bean;version=1.4.1
IcedTea
class,jar
Yes
application/x-java-bean;version=1.4.2
IcedTea
class,jar
Yes
application/x-java-bean;version=1.5
IcedTea
class,jar
Yes
application/x-java-bean;version=1.6
IcedTea
class,jar
Yes
application/x-java-bean;version=1.7
IcedTea
class,jar
Yes
application/x-java-bean;jpi-version=1.7.0_00
IcedTea
class,jar
Yes
Totem Web Browser Plugin 2.20.0
        File name: libtotem-basic-plugin.so
        The Totem 2.20.0 plugin handles video and audio streams.
    MIME Type
   Description
     Suffixes
     Enabled
application/ogg
Ogg multimedia
ogg
Yes
audio/ogg
Ogg Audio
ogg
Yes
audio/x-ogg
Ogg Audio
ogg
Yes
video/ogg
Ogg Video
ogg
Yes
video/x-ogg
Ogg Video
ogg
Yes
video/mpeg
MPEG video
mpg, mpeg, mpe
Yes
audio/wav
WAV audio
wav
Yes
audio/x-wav
WAV audio
wav
Yes
audio/mpeg
MP3 audio
mp3
Yes
application/x-nsv-vp3-mp3
NSV video
nsv
Yes
video/flv
Flash video
flv
Yes
Windows Media Player Plug-in 10 (compatible; Totem)
        File name: libtotem-gmp-plugin.so
        The Totem 2.20.0 plugin handles video and audio streams.
    MIME Type
   Description
     Suffixes
     Enabled
application/x-mplayer2
AVI video
avi, wma, wmv
Yes
video/x-ms-asf-plugin
ASF video
asf, wmv
Yes
video/x-msvideo
AVI video
asf, wmv
Yes
video/x-ms-asf
ASF video
asf
Yes
video/x-ms-wmv
WMV video
wmv
Yes
video/x-wmv
WMV video
wmv
Yes
video/x-ms-wvx
Playlist
wmv
Yes
video/x-ms-wm
ASF video
wmv
Yes
application/x-ms-wms
WMV video
wms
Yes
application/asx
Playlist
asx
Yes
DivX® Web Player
        File name: libtotem-mully-plugin.so
        The Totem 2.20.0 plugin handles video and audio streams.
    MIME Type
   Description
     Suffixes
     Enabled
video/divx
AVI video
divx
Yes
QuickTime Plug-in 7.2.0
        File name: libtotem-narrowspace-plugin.so
        The Totem 2.20.0 plugin handles video and audio streams.
    MIME Type
   Description
     Suffixes
     Enabled
video/quicktime
QT video
mov
Yes
video/mp4
MPEG-4 video
mp4
Yes
image/x-macpaint
MacPaint Bitmap
image
pntg
Yes
image/x-quicktime
Macintosh
Quickdraw/PICT
drawing
pict, pict1, pict2
Yes
video/x-m4v
MPEG-4 video
m4v
Yes
GCJ Web Browser Plugin 0.92
        File name: libgcjwebplugin.so
        The GCJ Web Browser Plugin executes Java applets.
    MIME Type
   Description
     Suffixes
     Enabled
application/x-java-vm
GCJ
class,jar
Yes
application/x-java-applet
GCJ
class,jar
Yes
application/x-java-applet;version=1.1
GCJ
class,jar
Yes
application/x-java-applet;version=1.1.1
GCJ
class,jar
Yes
application/x-java-applet;version=1.1.2
GCJ
class,jar
Yes
application/x-java-applet;version=1.1.3
GCJ
class,jar
Yes
application/x-java-applet;version=1.2
GCJ
class,jar
Yes
application/x-java-applet;version=1.2.1
GCJ
class,jar
Yes
application/x-java-applet;version=1.2.2
GCJ
class,jar
Yes
application/x-java-applet;version=1.3
GCJ
class,jar
Yes
application/x-java-applet;version=1.3.1
GCJ
class,jar
Yes
application/x-java-applet;version=1.4
GCJ
class,jar
Yes
application/x-java-applet;version=1.4.1
GCJ
class,jar
Yes
application/x-java-applet;version=1.4.2
GCJ
class,jar
Yes
application/x-java-applet;jpi-version=1.4.2_01
GCJ
class,jar
Yes
application/x-java-bean
GCJ
class,jar
Yes
application/x-java-bean;version=1.1
GCJ
class,jar
Yes
application/x-java-bean;version=1.1.1
GCJ
class,jar
Yes
application/x-java-bean;version=1.1.2
GCJ
class,jar
Yes
application/x-java-bean;version=1.1.3
GCJ
class,jar
Yes
application/x-java-bean;version=1.2
GCJ
class,jar
Yes
application/x-java-bean;version=1.2.1
GCJ
class,jar
Yes
application/x-java-bean;version=1.2.2
GCJ
class,jar
Yes
application/x-java-bean;version=1.3
GCJ
class,jar
Yes
application/x-java-bean;version=1.3.1
GCJ
class,jar
Yes
application/x-java-bean;version=1.4
GCJ
class,jar
Yes
application/x-java-bean;version=1.4.1
GCJ
class,jar
Yes
application/x-java-bean;version=1.4.2
GCJ
class,jar
Yes
application/x-java-bean;jpi-version=1.4.2_01
GCJ
class,jar
Yes

On Mon, 2007-12-03 at 18:43 +0000, Ubuntu Forums wrote:
> Dear gorlando,

---

### Post by rsambuca on 2007-12-03
You have installed the wrong version of java somehow.  You are using the Icedtea java rather than Sun-java.  Try opening your Synaptic Package Manager and searching for "icedtea".   Completely remove anything that is installed with icedtea in its name.

---

### Post by gorlando on 2007-12-03
originally icedtea was not installed and i installed it.

i have removed it.

i closed firefox and restarted and still get 

The following error has occurred:
Java Not Found or Not Working

in synaptic i have the following installed

java common
libhsqldb-java
libjaxp1.3-java
libjline-java
libservlet2.4-java
libxalan2-java
libxerces2-java
openoffice.org-java-common
sun-java6-bin
sun-java6-fonts
sun-java6-jre
sun-java6-plugin

---

### Post by gorlando on 2007-12-03
......

---

### Post by gorlando on 2007-12-04
I have followed all of the instructions that all of you good people have given and i still can't get java on my system properly.

is there anyone that can help or is there somewhere else i can get help?

When i do a verify on java.com it tells me my version is 1.4 ?

i even tried to follow the ubuntu and java doc but i still can't figure it out.

please help

---

### Post by johnbanni on 2007-12-04
> **gorlando said:**
> I have followed all of the instructions that all of you good people have given and i still can't get java on my system properly.

is there anyone that can help or is there somewhere else i can get help?

When i do a verify on java.com it tells me my version is 1.4 ?

i even tried to follow the ubuntu and java doc but i still can't figure it out.

please help
Do you have Sun-Java SE 5.0 packet installed? I had and I removed it, so now there is only Sun-java SE 6.0 installed. My netbank is working like a charm now! :)

---

### Post by gorlando on 2007-12-04
I don't know how to tell if the SE 5.0 packet is installed.

I'm going to try and attach a screen shot maybe someone can see something wrong.

---

### Post by gorlando on 2007-12-04
can anyone determine what my problem is based on the below?
sorry to keep posting, but i want to get this done.

do i need to uncomment something in sources.list or add multiverse ?
why am i getting error with bash and no java version?


sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ttf-dustin kdeedu-data tango-icon-theme-common tango-icon-theme libmikmod2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  sun-java6-bin
Suggested packages:
  binfmt-support
Recommended packages:
  libnss-mdns gsfonts-x11
The following NEW packages will be installed:
  sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
0 upgraded, 4 newly installed, 0 to remove and 13 not upgraded.
Need to get 0B/32.7MB of archives.
After unpacking 93.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package sun-java6-bin.
(Reading database ... 102934 files and directories currently installed.)
Unpacking sun-java6-bin (from .../sun-java6-bin_6-03-0ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-03-0ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-fonts.
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6-03-0ubuntu2_all.deb) ...
Selecting previously deselected package sun-java6-plugin.
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-03-0ubuntu2_i386.deb) ...
Setting up sun-java6-bin (6-03-0ubuntu2) ...
No theme index file in '/usr/share/icons/sun-java6.png'.
If you really want to create an icon cache here, use --ignore-theme-index.

Setting up sun-java6-plugin (6-03-0ubuntu2) ...

Setting up sun-java6-jre (6-03-0ubuntu2) ...

Setting up sun-java6-fonts (6-03-0ubuntu2) ...
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.

gary@gary-desktop:~$ java -version
The program 'java' can be found in the following packages:
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * java-gcj-compat
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found



deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by rsambuca on 2007-12-04
Wow, I have no idea how you got your system so messed up.  Is this a fresh install or an upgrade from Feisty?

Try this in a terminal```
sudo update-alternatives --config java
```

---

### Post by gorlando on 2007-12-04
thanks for hanging in with me rsambuca.

my system got even more messed up because i installed gizmo, which is great, but they said to use bonjour, so i installed that, but they said that doesn't work with avila, or whatever it was, and i uninstalled that and that really screwed up my system.

so i have done a fresh install.

now i want to take this slowly.

java -version

java version "1.5.0"
gij (GNU libgcj) version 4.2.1 (Ubuntu 4.2.1-5ubuntu5)

now i want to play a game at yahoo games and it needs a plugin
choices are

gcj web browser plug in
java plugin se6
---- se5
iced tea

should i install one of those, or should i do something else from within ubuntu?

and should i still do what you said in your previous post?

thanks

gary

---

### Post by gorlando on 2007-12-04
similar problem with adobe flash.

i install it but go to the website and it says the plugin is missing

---

### Post by vikramsharma on 2007-12-04
> **gorlando said:**
> similar problem with adobe flash.

i install it but go to the website and it says the plugin is missing

What browser are you using, if you are using firefox copy libflashplayer.so and flashplayer.xpt to /usr/lib/firefox/plugins also /usr/lib/mozilla/plugins .  In case you have installed swiftfox or even firefox yourself you would have to manually install the plugin. For example

I have swiftfox folder in /usr/local/bin so I copied the plugin into the folder /usr/local/bin/swiftfox/plugins.  Hope that made some sense.

---

### Post by gorlando on 2007-12-04
using firefox.

sorry but copy those files from where?

---

### Post by vikramsharma on 2007-12-04
Download the file using this[ link]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz") .  Expand the downloaded .tar.gz file and run the flashplayerinstaller (you would have to use the sudo command to do that). Also you might want to install the plugin in /usr/lib/firefox, the installer would install the plugins in /usr/lib/mozilla by default.

---

### Post by gorlando on 2007-12-05
i did not see the xpt file, but i copied the other file and then ran a flash detector and it seems to be there.

what about java?  still not being recognized as installed.

---

### Post by gorlando on 2007-12-05
i installed the java 6 plugin and it seems to work now.

thanks all very much for help

---

### Post by rsambuca on 2007-12-05
> **gorlando said:**
> i installed the java 6 plugin and it seems to work now.

thanks all very much for help

The java 6 plugin from where?  In order to help others, please outline exactly what you did to fix this problem.

---

### Post by gorlando on 2007-12-05
from what i best determine, the following corrected my problems with java and adobe flash player, and enabled me to run the online games on pogo.com and yahoo.com.  I'm a beginner here, so I'm not certain if both were required, but I think so.

1. be sure the following are installed through applications - add/remove 

sun java 6 web start
macromedia flash plugin

2. install the java se 6 plug in when prompted by the program that requires java on the desired website

3. Download the flashplayer file using this link ([http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)) .  
Expand the file and in the expanded folder look for libflashplayer.so and flashplayer.xpt and copy those to files to /usr/lib/firefox/plugins and /usr/lib/mozilla/plugins you would require root permissions to do so (you can use sudo) for that.

---

### Post by amightyo on 2007-12-05
With great yearning to explore the capabilities of Ubuntu do I join this forum. I am very new in this environment. I also want to make use of Java on my system. 
I get this message when I try installing JAVA6 JRE
sun-java6-jre:
 Depends: java-common (>=0.24) but it is not installable
 Depends: sun-java6-bin but it is not going to be installed or
 	ia32-sun-java6-bin (=6-03-0ubuntu2) but it is not installable
and when I tried the config of JAVA I got the message
There is only 1 program which provides jave
/usr/bin/gij-4.2. Nothing to configure

I really need your good assistance
THanks:KS

---

### Post by rsambuca on 2007-12-05
> **amightyo said:**
> With great yearning to explore the capabilities of Ubuntu do I join this forum. I am very new in this environment. I also want to make use of Java on my system. 
I get this message when I try installing JAVA6 JRE
sun-java6-jre:
 Depends: java-common (>=0.24) but it is not installable
 Depends: sun-java6-bin but it is not going to be installed or
 	ia32-sun-java6-bin (=6-03-0ubuntu2) but it is not installable
and when I tried the config of JAVA I got the message
There is only 1 program which provides jave
/usr/bin/gij-4.2. Nothing to configure

I really need your good assistance
THanks:KS

Are you using 32bit or 64bit?
What method did you try to install it with?

---

### Post by baxterdog on 2007-12-05
Was just having a similar problem and got it fixed.

Background; had sun java installed a couple of weeks ago but a sites java didn't seem to render right to me, so removed, and when prompted I added the gcj plugin. This may or may not have been working right for all cases, but worked for that night.

Today I have been trying to view a page created by a built in web server on a measuement device on my bench at work. Firefox would give me the same messages as stated by the original poster.

So;

1) made sure that the sun java package was installed

```
sudo apt-get install sun-java6-plugin
```

2) Used Synaptic to remove gcj java plugin, (checked for icedtea as well, didn't have it)

3) Confirmed with 'about:plugins' in firefox

This didn't work until restarting firefox.


BTW, How do you enter a colon without the Razzer showing up instead?

---

### Post by amightyo on 2007-12-05
Thanks everyone. I guess I have done it.
I now see after running "sudo apt-get install sun-java6-jre" and then I went to the add&Remove programs to enable the JDK console. :)
Java version "1.6.0-03@
JAVA (TM) SE Runtime Environment
JAVA Hotpot.............
and the other verstion of JAVA was overridden I guess. Now I need assistance of the IDE to use on LINUX JAvabeans or Eclipse and how to go about installing the IDE. Well I will explore that in a second and give a feedback:guitar:

---

### Post by amightyo on 2007-12-05
rsambuca, thanks so much for your response as I am just seeing it's 64bits. I now have JRE and JDK installed as I said above but now I want to install an IDE that is compatible with ubuntu for JAVA
Thanks:guitar::popcorn:

---

### Post by amightyo on 2007-12-05
well, I guess it just gets easier. I have installed Eclipse. Thanks once more.:KS

---

### Post by amightyo on 2007-12-05
Well, Everything went well. I can run my JAVA program. but I wish to ask a question a bit off. How do I increase the swap memory as when I installed ubuntu yesterday I followed the instruction that stated 500MB and when I hibernate, it requires more memory.  Is there anyway I can increase it like in Windows? Thanks

---

### Post by vikramsharma on 2007-12-05
You can also get java from Sun Microsystem's Website [http://java.sun.com](http://java.sun.com), download the the bin version and run the installer.  You might have to move the .bin (the java installer file) to the folder you want java to be installed to (for example I moved it to /usr/local/bin).  ONe more thing you would have to change the permission of the .bin file you download so that it can be executed that can be done through 'sudo chmod +x filename'.  After the installation all you would have to do is to link java plugin to your mozilla/firefox plugins folder in /usr/lib. Sorry, I think I am went into into verbose mode here,

---

### Post by 1967tempest on 2007-12-05
I was having the same problem.  After I made sure that the Java 1.6 was installed correctly I looked at "about:plugins" in Firefox.  I noticed that the GCL1.4 was very coincidental to the Java version the website said I had .  So i searched for GCL and this is what I marked for complete removal from the synaptic manager.


gcjwebplugin-4.2
Web browser plugin to execute Java (tm) applets

Pogo ga,e swork like a charm.  Took me a while but I am slowly moving away from Winblows.

Dave

---

### Post by rsambuca on 2007-12-06
> **amightyo said:**
> Well, Everything went well. I can run my JAVA program. but I wish to ask a question a bit off. How do I increase the swap memory as when I installed ubuntu yesterday I followed the instruction that stated 500MB and when I hibernate, it requires more memory.  Is there anyway I can increase it like in Windows? Thanks

You will have to shrink another partition and expand the swap.  I recommend doing this with the [gParted liveCD]("http://gparted-livecd.tuxfamily.org/").

---

### Post by ChuTai on 2007-12-06
Hi guys
I'm pretty new to ubuntu as well
I still can't get the java plugin to work for firefox

when i type in
```
sudo apt-get install sun-java6-plugin
```

it says 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

what should I do??

---

### Post by rsambuca on 2007-12-06
> **ChuTai said:**
> Hi guys
I'm pretty new to ubuntu as well
I still can't get the java plugin to work for firefox

when i type in
```
sudo apt-get install sun-java6-plugin
```

it says 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

what should I do??
You have to enable the software repositories that contain the java package first.  To do so, go to System - Administration - Software Sources.  Check the box for the Multiverse repositories.  Close the window and then update your sources when prompted.  You will then be able to install the package.

---

### Post by froy02 on 2007-12-06
I had this problem before and what i did was removed all the java  related items java- common, sun-java stuff. I used synaptics package manager to remove all that java stuff. I think i removed the icedtea stuff also.

Then I installed ubuntu-restricted-extras and it installed several items inluding java-6 properly.

---

### Post by ChuTai on 2007-12-06
Haha i thought no one was answering but my post was the last one on pg 4 lol

Anyways,
I already had Multiverse enabled and when I used synaptic to uninstall java and then reinstalled the ubuntu-restricted-extras it didn't do anything.

i tried 
```
sudo apt-get install sun-java6-plugin
```
it still prints out 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

what should I try to get all of java working now?

---

### Post by kenklay on 2007-12-14
> **baxterdog said:**
> Was just having a similar problem and got it fixed.

Background; had sun java installed a couple of weeks ago but a sites java didn't seem to render right to me, so removed, and when prompted I added the gcj plugin. This may or may not have been working right for all cases, but worked for that night.

Today I have been trying to view a page created by a built in web server on a measuement device on my bench at work. Firefox would give me the same messages as stated by the original poster.

So;

1) made sure that the sun java package was installed

```
sudo apt-get install sun-java6-plugin
```

2) Used Synaptic to remove gcj java plugin, (checked for icedtea as well, didn't have it)

3) Confirmed with 'about:plugins' in firefox

This didn't work until restarting firefox.


BTW, How do you enter a colon without the Razzer showing up instead?

:)Thanks for the hint on gcjwebplugin. I spent hours looking in the forums and tried various suggestions and that was the trick to getting java to work in Firefox for me.

---

### Post by crunchfighter on 2007-12-19
Hi, new poster here.
I've tried all the steps in this thread with no luck.  (except the one with yahoo, don't use their site)
No icedtea
removed gcj plugins
reinstalled java6 several times with synaptic and terminal
I get a good version output in the terminal, but the java website gives me a failing grade.  
I'd like to put in a screenshot here.  Let's see how I do:

Not sure it worked.  Tried it as an attachment.

about:plugins output as a screenshot:

Additionally, I cannot install a java-based program that gives me an error that it does not detect jvm 1.5.  java -version shows the current version.  Firefox does not.

---

### Post by Seigneus on 2007-12-24
I am  having the same exact problem as the previous users. I've uninstalled, re-installed and used every method I could find on the internet in order to get Java to work. None have been successful. The only time the browser detected a plug-in was when I had Blackdown version 1.4 installed. But of course, none of the websites would accept the version. I am a 32-bit user with Ubuntu 7.10 and i'm using Firefox browser. And of course, I've already tried all the previous methods in this thread. Any help will be greatly appreciated. I'm trying to leave Windows cold-turkey, but this is one roadblock that's making it difficult to do so.

---

### Post by crunchfighter on 2007-12-25
I started over.  I ordered ordered some recovery CDs and put XP back on the machine.  I am working out the details of partitioning the drive (having trouble and I don't want to accidentally overwrite windows, so it's taking some time) 

I am hoping that the reinstall will make things easier since I probably gooned something up horribly the first time around since I was installing/uninstalling like a madman.  I'll let you know.

Craig

---

### Post by itzame on 2007-12-26
I was havin' the same problem had latest java installed i think the gcjwebplugin is hosin' things up
remove gcjwebplugin stuff and see if that helps...IWFM

---

### Post by QKC on 2008-04-08
Hi i am new to Ubuntu also,having the same problem installing Java. Would appreciate all the help. Below is my ubuntu details. Appreciate all the steps installation


quek@quek-laptop:~$ uname -a
Linux quek-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
quek@quek-laptop:~$ sudo apt-get install sun-java6-plugin
[sudo] password for quek:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-plugin
quek@quek-laptop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras
quek@quek-laptop:~$

---

