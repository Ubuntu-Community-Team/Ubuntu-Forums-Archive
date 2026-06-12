---
title: "Flash working for anyone?"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zekopeko on 2008-10-13
as per the title.

it's installed but firefox won't pick it up.

---

### Post by shuttleworthwannabe on 2008-10-13
i was just about to post this too; anyway, any luck with Flash in FF and also does it play with sound? 
I am using kernel *-7; pulse audio
sound works on my laptop but no sound in Flash animation though.

---

### Post by philinux on 2008-10-13
Working fine here. Latest nvidia driver and latest kernel. In fact it was only sound in flash that wasn't working. That got fixed a couple of weeks ago with an update.

---

### Post by shuttleworthwannabe on 2008-10-13
lucky you, then.

---

### Post by philinux on 2008-10-13
The OP did ask the question. I've not used any workarounds to fix things. Things got fixed via the normal updates.

Maybe a full reinstall is needed.

---

### Post by homemadejam on 2008-10-13
What version of Flash are you using?

Jam

---

### Post by Sef on 2008-10-13
1) Are you using 32 or 64-bit Ibex?

2) How did you install flash?

---

### Post by jerrylamos on 2008-10-13
Ubuntu Beta Flash 10.0 r12 video working on IBM Thinkpad R31, 32 bit Celeron 1gHz.  Sound does not, Intel 82801CA-ICH3 (Alsa Mixer).  

Flash was installed with Synaptic as part of ubuntu-restricted-extras.

I'm dual booted with Alpha 5, NOT UPDATED!!! Flash & sound working except some artifacts, snow, on the video.

Jerry

---

### Post by Lorenz on 2008-10-13
> **zekopeko said:**
> as per the title.

it's installed but firefox won't pick it up.

same problem here, tried removing and installing it, installing it manually, etc. Won't work. FF doesn't pick it up, as you said.

---

### Post by xebian on 2008-10-13
There are so many 'how to flash' around, but IMHO the only foolproof, correct and proper way is to install the flashplugin-nonfree metapackage especially if you are running 64-bit.

---

### Post by smartboyathome on 2008-10-13
Flash is working fine here installed from the repos.

---

### Post by zekopeko on 2008-10-13
i'm running 32bit ibex and i installed it with synaptic but firefox still doesn't pick it up. youtube is asking me to install flash and noscript isn't blocking youtube.
firefox even offers to install flash for me and says that it's already installed but still it's a no go. really weird.

i upgraded so it could be that i have a symlink from before (i was playing with flash 10beta on hardy). could somebody tell me where should flash be installed and symlinked?

---

### Post by philinux on 2008-10-13
Use places search and look for

libflashplayer.so

---

### Post by zekopeko on 2008-10-13
here it is 

~$ locate libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so

and there isn't a symlink that i can see (visually from nautilus.should there be a symlink to the firefox plugins folder?)

---

### Post by philinux on 2008-10-13
Thats correct thats all I've got. 

Try closing firefox, browse to the .mozilla folder in home. Show hidden files. Navigate to the profile folder ????????.default.
Delete xpti.dat then restart firefox.

Other than that back up your bookmarks and delete the .mozilla folder altogether and let FF create a new one.

---

### Post by zekopeko on 2008-10-13
it's still not working. i completely deleted/moved the .mozilla folder.

---

### Post by kansasnoob on 2008-10-13
Hmmm, flash is working great here in Intrepid. You can see what's installed by typing:

> about:PLUGINS

Note: plugins can be either upper or lower case, but if I use lower case I get this :p.

In addition to flashplugin-nonfree I install ALL sun-java6-**** EXCEPT -doc and -source, and also flashblock (or noscript), and mozilla-plugin-vlc and all vlc plugins (I remove totem-mozilla).

And I've found that sometimes just restarting Firefox doesn't get the changes to apply so I usually restart the desktop: Ctrl > Alt > Backspace.

The only other thing I can think of is checking which version of Firefox you have running.

---

### Post by zekopeko on 2008-10-13
i checked ```
about:plugins
``` and there isn't a section about flash. i have totem and java installed

---

### Post by philinux on 2008-10-13
All i can suggest is completely removing flashplugin-nonfree and reinstalling it. Maybe reboot too.

---

### Post by quazi on 2008-10-13
Flash works great for me in Intrepid except for one site (and it used to work there in Hardy):  [www.grooveshark.com](www.grooveshark.com)

When I search for a song/artist, firefox takes me to a blank screen.  Can anyone get that site to work?

---

### Post by kansasnoob on 2008-10-13
> **zekopeko said:**
> i checked ```
about:plugins
``` and there isn't a section about flash. i have totem and java installed


I wrote that poorly. Type about:plugins in the URL window of Firefox and you'll get a list like this:

> Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r12

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
Java(TM) Plug-in 1.6.0_07-b06

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_07

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_07 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_07 	Java 		Yes
VLC Multimedia Plug-in

    File name: libvlcplugin.so
    Version 0.9.4 Grishenko, copyright 1996-2007 The VideoLAN Team
    [http://www.videolan.org/](http://www.videolan.org/)

MIME Type 	Description 	Suffixes 	Enabled
audio/mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
audio/x-mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
video/mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/x-mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/x-mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/mp4 	MPEG-4 video 	mp4,mpg4 	Yes
audio/mp4 	MPEG-4 audio 	mp4,mpg4 	Yes
application/mpeg4-iod 	MPEG-4 video 	mp4,mpg4 	Yes
application/mpeg4-muxcodetable 	MPEG-4 video 	mp4,mpg4 	Yes
video/x-msvideo 	AVI video 	avi 	Yes
video/quicktime 	QuickTime video 	mov,qt 	Yes
application/x-ogg 	Ogg stream 	ogg 	Yes
application/ogg 	Ogg stream 	ogg 	Yes
application/x-vlc-plugin 	VLC plug-in 	vlc 	Yes
video/x-ms-asf-plugin 	Windows Media Video 	asf,asx 	Yes
video/x-ms-asf 	Windows Media Video 	asf,asx 	Yes
application/x-mplayer2 	Windows Media 		Yes
video/x-ms-wmv 	Windows Media 	wmv 	Yes
video/x-ms-wvx 	Windows Media Video 	wvx 	Yes
application/x-google-vlc-plugin 	Google VLC plug-in 		Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/3gpp 	3GPP audio 	3gp,3gpp 	Yes
video/3gpp 	3GPP video 	3gp,3gpp 	Yes
audio/3gpp2 	3GPP2 audio 	3g2,3gpp2 	Yes
video/3gpp2 	3GPP2 video 	3g2,3gpp2 	Yes
video/divx 	DivX video 	divx 	Yes
video/flv 	FLV video 	flv 	Yes
video/x-flv 	FLV video 	flv 	Yes
video/x-matroska 	Matroska video 	mkv 	Yes
audio/x-matroska 	Matroska audio 	mka 	Yes


---

### Post by zekopeko on 2008-10-13
well i did check in firefox the about:plugins, and i know about:config and about:mozilla pages.
i know my why around ubuntu/linux.

---

### Post by MALEADt on 2008-10-13
Doesn't work in here too: makes firefox & X spike to full cpu, and works very laggy. Works fine on another pc though, maybe a reinstall will work it out (gonna wait till final).

---

### Post by Lorenz on 2008-10-13
I have got the identical problem as zekopeko.
Did all the steps that were recommended here (not that I hadn't done them before already). Bottom line: Flash installed, but firefox doesn't pick it up.

---

### Post by philinux on 2008-10-13
Like I suggested before. Reinstall from a daily build.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by swj on 2008-10-13
I did have some minor flash issues (video artifacts) every once and while.  Since the flash update (the other day?), I don't think I am having any more issues...I'll check it out tonight.

---

### Post by zekopeko on 2008-10-13
well i fixed it by doing a clean install. but somebody should file a bug.

---

### Post by philinux on 2008-10-13
> **zekopeko said:**
> well i fixed it by doing a clean install. but somebody should file a bug.

It could be some workarounds that you did. That's why i suggested a clean install.

---

### Post by DougieFresh4U on 2008-10-13
> **zekopeko said:**
> as per the title.

it's installed but firefox won't pick it up.

I am watching youtube, no problems at all

---

