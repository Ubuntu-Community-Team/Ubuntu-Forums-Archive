---
title: "How to get JVM up and running?"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by cstoh on 2008-05-23
I upgraded from 7.10 to 8.04. It took me many attempts before I succeeded. Everything seems to work fine except when I try to login to some bank sites I get the message that either I did not enable Java or that my Java Virtual Machine is not running. I checked the browser and Java is enabled. So how do I get the Java Virtual Machine to work?
Thanks in advance

---

### Post by jamesstansell on 2008-05-24
Many people are reporting banking applications that do not currently work with the browser plugin currently available with the openjdk6 java.  For now try installing the the sun-java6-plugin package.

Hmm - the phrase "Java is enabled" could mean two different things to me.  If you're looking at the browser optin "enable Java" that may not mean that Java is installed and ready to run. (Personally I think that option should be retired.)

In order for a Java applet to run the Java plugin needs to be available.  The browserspy page [http://gemal.dk/browserspy/plugins_detail.html](http://gemal.dk/browserspy/plugins_detail.html) is a good way to check that out.

---

### Post by binary00mind on 2008-05-24
> **cstoh said:**
> I upgraded from 7.10 to 8.04. It took me many attempts before I succeeded. Everything seems to work fine except when I try to login to some bank sites I get the message that either I did not enable Java or that my Java Virtual Machine is not running. I checked the browser and Java is enabled. So how do I get the Java Virtual Machine to work?
Thanks in advanceHi, It could be many reasons or combination of them. Your JAVA could be on but unknowingly You may have some restriction on. Like resizing windows or most likely changing text in the banner. And it could be done by third party add-on (I am only speculating. I don't know the browser YOU are using ) like in firefox, just to name the few; Web Developer. No Script or Cookie Safe, they all could do the dirty work against You. Actually the real JVM (Java Virtual Mchine )by IBM lost ground. They not aggresive enough to keep developing. Anyway in Ubuntu the real JVM is under name of "Cacao" I Do have Installed JVM aka Cacao with some "recent" upgrade, and sometimes I Do use it. (on Konqueror) Also make sure that aplet has enough live-time to do it's work (for your bank)...Pure speculating. Now Sun Jva#7 is the name of the game..Put the error console on, and on purpose do some "dry runs" in the spyworld of Internet..Good Luck

---

### Post by cstoh on 2008-05-26
> **binary00mind said:**
> Hi, It could be many reasons or combination of them. Your JAVA could be on but unknowingly You may have some restriction on. Like resizing windows or most likely changing text in the banner. And it could be done by third party add-on (I am only speculating. I don't know the browser YOU are using ) like in firefox, just to name the few; Web Developer. No Script or Cookie Safe, they all could do the dirty work against You. Actually the real JVM (Java Virtual Mchine )by IBM lost ground. They not aggresive enough to keep developing. Anyway in Ubuntu the real JVM is under name of "Cacao" I Do have Installed JVM aka Cacao with some "recent" upgrade, and sometimes I Do use it. (on Konqueror) Also make sure that aplet has enough live-time to do it's work (for your bank)...Pure speculating. Now Sun Jva#7 is the name of the game..Put the error console on, and on purpose do some "dry runs" in the spyworld of Internet..Good Luck

I tried installing Cacao but after that I still get the same problem of not being able to open the page. This time it does not tell me that JVM not running. It just says that the page cannot run the applet. I've also made sure that java can resize windows and all that.
Can someone help me and guide me as to what to do next? Thank you

---

### Post by binary00mind on 2008-05-27
[FONT="Tahoma"][COLOR="DarkRed"][/COLOR][/FONT][CENTER][/CENTERHi Sorry to hear that the issue is still unsolved. It is hard to speculate long distance. I wish I knew what browser You are using.(Unless I missed that)
Anyhow JVM from Ubuntu comes with regular dependencies, like any other package. Do search in Synaptics under name "JVM" Name plus description. You will get more results. just like that. You shall see a lot of add-ons or utilities-If You Will- That work together with JVM (There is a updated version under different name.(it slipped my mind now the name) plus install the java fonts from "Sun" 5 or 6.
All this (especially the fonts) is really an Overkill. The security of Your bank is-I guess-doing it's own overkill. Maybe they digging deep into Your Privacy (not that You were picked out) in terms of veryfing if You is really You.
The Java as We all know, is a perfect tool to do tricky things, especially in Windows. They, (the bank) maybe did not adjust enough for Linux. Which is doubtfull because most script writers, do their work on Linux platform.
Ubuntu system, or Your Firewall is preventing all that, to sneak in. That is very possible. Pure speculation.
I am curious, how it all ends. I Will Stay Tuned. Good Luck

---

### Post by jamesstansell on 2008-05-28
> **cstoh said:**
> 
Can someone help me and guide me as to what to do next? Thank you

Did you try the sun-java6-plugin package?  If it doesn't work at first there are other recent threads here (look for the java tag) that explain how to use update-alternatives.

---

### Post by cstoh on 2008-05-29
> **jamesstansell said:**
> Did you try the sun-java6-plugin package?  If it doesn't work at first there are other recent threads here (look for the java tag) that explain how to use update-alternatives.

I´ve got sun-java6-plugin installed. It does not seem to help. I had sun-java5 installed also. Is it necessary?

---

### Post by cstoh on 2008-05-29
> **jamesstansell said:**
> Many people are reporting banking applications that do not currently work with the browser plugin currently available with the openjdk6 java.  For now try installing the the sun-java6-plugin package.

Hmm - the phrase "Java is enabled" could mean two different things to me.  If you're looking at the browser optin "enable Java" that may not mean that Java is installed and ready to run. (Personally I think that option should be retired.)

In order for a Java applet to run the Java plugin needs to be available.  The browserspy page [http://gemal.dk/browserspy/plugins_detail.html](http://gemal.dk/browserspy/plugins_detail.html) is a good way to check that out.

Here is the output of the link you gave. Please advice if anything is missing

Variable 	Setting
Plugin Directories


Shockwave Flash
Shockwave Flash 9.0 r124
Filename: libflashplayer.so
MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash   	Shockwave Flash   	swf   	Yes  
application/futuresplash   	FutureSplash Player   	spl   	Yes  

QuickTime Plug-in 6.0 / 7
mplayerplug-in 3.50

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
JavaScript Enabled and Using GTK2 Widgets
Filename: mplayerplug-in-qt.so
MIME Type 	Description 	Suffixes 	Enabled
video/quicktime   	Quicktime   	mov   	Yes  
video/x-quicktime   	Quicktime   	mov   	Yes  
image/x-quicktime   	Quicktime   	mov   	Yes  
video/quicktime   	Quicktime   	mp4   	Yes  
video/quicktime   	Quicktime - Session Description Protocol   	sdp   	Yes  
application/x-quicktimeplayer   	Quicktime   	mov   	Yes  

Windows Media Player Plugin
mplayerplug-in 3.50

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
JavaScript Enabled and Using GTK2 Widgets
Filename: mplayerplug-in-wmp.so
MIME Type 	Description 	Suffixes 	Enabled
application/asx   	Media Files   	*   	Yes  
video/x-ms-asf-plugin   	Media Files   	*   	Yes  
video/x-msvideo   	AVI   	avi,*   	Yes  
video/msvideo   	AVI   	avi,*   	Yes  
application/x-mplayer2   	Media Files   	*   	Yes  
application/x-ms-wmv   	Microsoft WMV video   	wmv,*   	Yes  
video/x-ms-asf   	Media Files   	asf,asx,*   	Yes  
video/x-ms-wm   	Media Files   	wm,*   	Yes  
video/x-ms-wmv   	Microsoft WMV video   	wmv,*   	Yes  
audio/x-ms-wmv   	Windows Media   	wmv,*   	Yes  
video/x-ms-wmp   	Windows Media   	wmp,*   	Yes  
application/x-ms-wmp   	Windows Media   	wmp,*   	Yes  
video/x-ms-wvx   	Windows Media   	wvx,*   	Yes  
audio/x-ms-wax   	Windows Media   	wax,*   	Yes  
audio/x-ms-wma   	Windows Media   	wma,*   	Yes  
application/x-drm-v2   	Windows Media   	asx,*   	Yes  
audio/wav   	Microsoft wave file   	wav,*   	Yes  
audio/x-wav   	Microsoft wave file   	wav,*   	Yes  

mplayerplug-in 3.50
mplayerplug-in 3.50

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
JavaScript Enabled and Using GTK2 Widgets
Filename: mplayerplug-in.so
MIME Type 	Description 	Suffixes 	Enabled
video/mpeg   	MPEG   	mpg,mpeg   	Yes  
audio/mpeg   	MPEG   	mpg,mpeg   	Yes  
video/x-mpeg   	MPEG   	mpg,mpeg   	Yes  
video/x-mpeg2   	MPEG2   	mpv2,mp2ve   	Yes  
audio/mpeg   	MPEG   	mpg,mpeg   	Yes  
audio/x-mpeg   	MPEG   	mpg,mpeg   	Yes  
audio/mpeg2   	MPEG audio   	mp2   	Yes  
audio/x-mpeg2   	MPEG audio   	mp2   	Yes  
video/mp4   	MPEG 4 Video   	mp4   	Yes  
video/3gpp   	MPEG 4 Video   	mp4,3gp   	Yes  
audio/mpeg3   	MPEG audio   	mp3   	Yes  
audio/x-mpeg3   	MPEG audio   	mp3   	Yes  
audio/x-mpegurl   	MPEG url   	m3u   	Yes  
audio/mp3   	MPEG audio   	mp3   	Yes  
application/x-ogg   	Ogg Vorbis Media   	ogg   	Yes  
audio/ogg   	Ogg Vorbis Audio   	ogg   	Yes  
audio/x-ogg   	Ogg Vorbis Audio   	ogg   	Yes  
application/ogg   	Ogg Vorbis / Ogg Theora   	ogg   	Yes  
audio/flac   	FLAC Audio   	flac   	Yes  
audio/x-flac   	FLAC Audio   	flac   	Yes  
video/fli   	FLI animation   	fli,flc   	Yes  
video/x-fli   	FLI animation   	fli,flc   	Yes  
video/x-flv   	Flash Video   	flv   	Yes  
video/vnd.vivo   	VivoActive   	viv,vivo   	Yes  
application/x-nsv-vp3-mp3   	Nullsoft Streaming Video   	nsv   	Yes  
audio/x-mod   	Soundtracker   	mod   	Yes  
audio/basic   	Basic Audio File   	au,snd   	Yes  
audio/x-basic   	Basic Audio File   	au,snd   	Yes  
audio/x-scpls   	Shoutcast Playlist   	pls   	Yes  

Default Plugin
The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.
Filename: libnullplugin.so
MIME Type 	Description 	Suffixes 	Enabled
*   	All types   	.*   	Yes  

Demo Print Plugin for unix/linux
The demo print plugin for unix.
Filename: libunixprintplugin.so
MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin   	Demo Print Plugin for Unix/Linux   	.pnt   	Yes  

iTunes Application Detector
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.
Filename: librhythmbox-itms-detection-plugin.so
MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin   	  	  	Yes  

VLC Multimedia Plugin
Version 0.8.6e Janus, copyright 1996-2007 The VideoLAN Team
[http://www.videolan.org/](http://www.videolan.org/)
Filename: libvlcplugin.so
MIME Type 	Description 	Suffixes 	Enabled
audio/mpeg   	MPEG audio   	mp2,mp3,mpga,mpega   	Yes  
audio/x-mpeg   	MPEG audio   	mp2,mp3,mpga,mpega   	Yes  
video/mpeg   	MPEG video   	mpg,mpeg,mpe   	Yes  
video/x-mpeg   	MPEG video   	mpg,mpeg,mpe   	Yes  
video/mpeg-system   	MPEG video   	mpg,mpeg,mpe,vob   	Yes  
video/x-mpeg-system   	MPEG video   	mpg,mpeg,mpe,vob   	Yes  
video/mpeg4   	MPEG-4 video   	mp4,mpg4   	Yes  
audio/mpeg4   	MPEG-4 audio   	mp4,mpg4   	Yes  
application/mpeg4-iod   	MPEG-4 video   	mp4,mpg4   	Yes  
application/mpeg4-muxcodetable   	MPEG-4 video   	mp4,mpg4   	Yes  
video/x-msvideo   	AVI video   	avi   	Yes  
video/quicktime   	QuickTime video   	mov,qt   	Yes  
application/x-ogg   	Ogg stream   	ogg   	Yes  
application/ogg   	Ogg stream   	ogg   	Yes  
application/x-vlc-plugin   	VLC plugin   	vlc   	Yes  
video/x-ms-asf-plugin   	Windows Media Video   	asf,asx   	Yes  
video/x-ms-asf   	Windows Media Video   	asf,asx   	Yes  
application/x-mplayer2   	Windows Media   	  	Yes  
video/x-ms-wmv   	Windows Media   	wmv   	Yes  
application/x-google-vlc-plugin   	Google VLC plugin   	  	Yes  
audio/wav   	WAV audio   	wav   	Yes  
audio/x-wav   	WAV audio   	wav   	Yes  
audio/3gpp   	3GPP audio   	3gp,3gpp   	Yes  
video/3gpp   	3GPP video   	3gp,3gpp   	Yes  
audio/3gpp2   	3GPP2 audio   	3g2,3gpp2   	Yes  
video/3gpp2   	3GPP2 video   	3g2,3gpp2   	Yes  

GCJ Web Browser Plugin (using IcedTea) 1.0
The GCJ Web Browser Plugin (using IcedTea) executes Java applets.
Filename: gcjwebplugin.so
MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm   	IcedTea   	class,jar   	Yes  
application/x-java-applet   	IcedTea   	class,jar   	Yes  
application/x-java-applet;version=1.1   	IcedTea   	class,jar   	Yes  
application/x-java-applet;version=1.1.1   	IcedTea   	class,jar   	Yes  
application/x-java-applet;version=1.1.2   	IcedTea   	class,jar   	Yes  
application/x-java-applet;version=1.1.3   	IcedTea   	class,jar   	Yes  
application/x-java-applet;version=1.2   	IcedTea   	class,jar   	Yes  
application/x-java-applet;version=1.2.1   	IcedTea   	class,jar   	Yes  
application/x-java-applet;version=1.2.2   	IcedTea   	class,jar   	Yes  
application/x-java-applet;version=1.3   	IcedTea   	class,jar   	Yes  
application/x-java-applet;version=1.3.1   	IcedTea   	class,jar   	Yes  
application/x-java-applet;version=1.4   	IcedTea   	class,jar   	Yes  
application/x-java-applet;version=1.4.1   	IcedTea   	class,jar   	Yes  
application/x-java-applet;version=1.4.2   	IcedTea   	class,jar   	Yes  
application/x-java-applet;version=1.5   	IcedTea   	class,jar   	Yes  
application/x-java-applet;version=1.6   	IcedTea   	class,jar   	Yes  
application/x-java-applet;jpi-version=1.6.0_00   	IcedTea   	class,jar   	Yes  
application/x-java-bean   	IcedTea   	class,jar   	Yes  
application/x-java-bean;version=1.1   	IcedTea   	class,jar   	Yes  
application/x-java-bean;version=1.1.1   	IcedTea   	class,jar   	Yes  
application/x-java-bean;version=1.1.2   	IcedTea   	class,jar   	Yes  
application/x-java-bean;version=1.1.3   	IcedTea   	class,jar   	Yes  
application/x-java-bean;version=1.2   	IcedTea   	class,jar   	Yes  
application/x-java-bean;version=1.2.1   	IcedTea   	class,jar   	Yes  
application/x-java-bean;version=1.2.2   	IcedTea   	class,jar   	Yes  
application/x-java-bean;version=1.3   	IcedTea   	class,jar   	Yes  
application/x-java-bean;version=1.3.1   	IcedTea   	class,jar   	Yes  
application/x-java-bean;version=1.4   	IcedTea   	class,jar   	Yes  
application/x-java-bean;version=1.4.1   	IcedTea   	class,jar   	Yes  
application/x-java-bean;version=1.4.2   	IcedTea   	class,jar   	Yes  
application/x-java-bean;version=1.5   	IcedTea   	class,jar   	Yes  
application/x-java-bean;version=1.6   	IcedTea   	class,jar   	Yes  
application/x-java-bean;jpi-version=1.6.0_00   	IcedTea   	class,jar   	Yes

---

### Post by jamesstansell on 2008-05-30
> **cstoh said:**
> I´ve got sun-java6-plugin installed. It does not seem to help. I had sun-java5 installed also. Is it necessary?

Based on your other post it looks like you have icedtea-gcjwebplugin (the default java plugin in hardy) installed OK.  I'm guessing it must not be compatible with the web site that you want to use.

At this point I would recommend that you get sun-java6-plugin working.  Uninstall the sun-java5-plugin and icedtea-gcjwebplugin packages.  Then run "update-java-alternatives -s java-6-sun".

(Theoretically the update-java-alternatives command should work without needing to first remove the other plugin packages, but Hardy shipped with a packaging bug, and removing the other packages is a work-around.  Hopefully an update will fix the bug before long.)

---

### Post by cstoh on 2008-05-30
> **jamesstansell said:**
> Based on your other post it looks like you have icedtea-gcjwebplugin (the default java plugin in hardy) installed OK.  I'm guessing it must not be compatible with the web site that you want to use.

At this point I would recommend that you get sun-java6-plugin working.  Uninstall the sun-java5-plugin and icedtea-gcjwebplugin packages.  Then run "update-java-alternatives -s java-6-sun".

(Theoretically the update-java-alternatives command should work without needing to first remove the other plugin packages, but Hardy shipped with a packaging bug, and removing the other packages is a work-around.  Hopefully an update will fix the bug before long.)

Thanks for your help. Now I do not get the message about JVM nor ¨applet not started¨ but I guess there is still some incompatibility because it says that an applet need run the application did not load correctly. Frankly, that could mean anything. They probably wouldn´t to reveal the inner workings of their site so I probably would not be able to work this out. Thanks anyway

---

### Post by cstoh on 2008-06-01
> **cstoh said:**
> Thanks for your help. Now I do not get the message about JVM nor ¨applet not started¨ but I guess there is still some incompatibility because it says that an applet need run the application did not load correctly. Frankly, that could mean anything. They probably wouldn´t to reveal the inner workings of their site so I probably would not be able to work this out. Thanks anyway

I have an EeePC that runs on Xandos Linux. It is able to log in to the said bank site. I watched the status bar to see what applet is needed to run the app and it shows ¨e2e¨ applet. Does anybody know anything about such an applet?
Thanks in advance.

---

