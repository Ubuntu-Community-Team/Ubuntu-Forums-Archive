---
title: "Help! Ubuntu newbie!"
date: 2012-06-29
forum: Installation &amp; Upgrades
---

### Post by Cjames93 on 2012-06-29
How do i get flash player to work, it says i have it downloaded in the Ubuntu software centre but it wont work. i have deleted it and re downloaded it but it still wont work, i also tried to downloads from the Adobe website but it need a program to install it through but i don't have one, what can i do? any help appreciated.

---

### Post by Jimmyfj on 2012-06-29
You need to fire up a terminal **ctrl+alt+t** and install flash through restricted extras. But remember to un-install the flash that's not working first. In the terminal run this code:

```
sudo apt-get install ubuntu-restricted-extras
```

After this your flash should work.

---

### Post by Cjames93 on 2012-06-29
Right, i did what you said and it completed all the steps but my flash still is not working, do i need to do something else? 
Thanks

---

### Post by Jimmyfj on 2012-06-29
Which method did you use to un-install the previous version?

I'd recommend that you try un-install through Synaptic. Here you search for flash and when found you mark it for complete removal.

Before you try re-installing it try removing everything "gnash". It could be gnash who is conflicting on your system.

---

### Post by Cjames93 on 2012-06-29
Did the steps you said then re-installed flash through the terminal and it still wont work for me , i havent rebooted thought , could that be it?

---

### Post by Jimmyfj on 2012-06-29
> **Cjames93 said:**
> Did the steps you said then re-installed flash through the terminal and it still wont work for me , i havent rebooted thought , could that be it?

Reboot to get flash working shouldn't be necessary.

Which version does Synaptic say you have installed.

My Synaptic tells me that I have version 11.2.202.236 installed.

BTW - Which browser are you using? If it is Epiphany it makes sense. If the browser is Firefox it makes no sense.

Instead of rebooting your system try close all incidents of Firefox you have running and start a fresh browser.

---

### Post by lovinglinux on 2012-06-30
Try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/).

---

### Post by Cjames93 on 2012-07-01
I use Firefox and my synaptic says at the bottom " version: 0.63.1ubuntu7 (synaptic" , i installed flash-aid and used it to install flash but i still cant get it to work.
 thanks

---

### Post by goldshirt9 on 2012-07-01
> **lovinglinux said:**
> try [flash-aid]("https://addons.mozilla.org/en-us/firefox/addon/flash-aid/").
+1

---

### Post by lovinglinux on 2012-07-01
> **Cjames93 said:**
> I use Firefox and my synaptic says at the bottom " version: 0.63.1ubuntu7 (synaptic" , i installed flash-aid and used it to install flash but i still cant get it to work.
 thanks

Click "Help > Generate Report" in Flash-Aid menu and post the result here.

---

### Post by Cjames93 on 2012-07-01
```
Ubuntu Architecture  Linux DJames 2.6.32-41-generic #91-Ubuntu SMP Wed Jun 13 11:44:43 UTC 2012 i686 GNU/Linux  

Ubuntu Version  

DISTRIB_ID=Ubuntu DISTRIB_RELEASE=10.04 
DISTRIB_CODENAME=lucid 
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"  

Firefox Packages  

firefox						install 
firefox-branding				install 
firefox-gnome-support				install 
firefox-locale-en				install  

Firefox binaries 
 
/usr/bin/firefox: symbolic link to `../lib/firefox/firefox.sh' 

/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory) 

/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)  

Firefox divertion  

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)  

Sources  

google-chrome.list  

Flash packages  

Plugin locations   

/usr/lib/mozilla/plugins/flashplugin-alternative.so  

Flash symlinks   

/usr/lib/mozilla/plugins/libflashplayer.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped 

/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory) 

/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory) 

/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory) 

/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory) 

/usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory) 

/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory) 

/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory) 

/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory) 

/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory) 

/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)  

pluginreg.dat  

Generated File. Do not edit.  [HEADER] Version:0.15:$ Arch:x86-gcc3:$  

[PLUGINS] libflashplayer.so:$ /usr/lib/mozilla/plugins/libflashplayer.so:$ :$ 1336714805000:0:1:$ Shockwave Flash 11.2 r202:$ Shockwave Flash:$ 2 0:application/x-shockwave-flash:Shockwave Flash:swf:$ 1:application/futuresplash:FutureSplash Player:spl:$ 
]
```

---

### Post by Cjames93 on 2012-07-01
Thats all of it, although it all got squashed up together when i posted it.

---

### Post by lovinglinux on 2012-07-01
> **Cjames93 said:**
> Thats all of it, although it all got squashed up together when i posted it.

Please use the code tags.

---

### Post by Cjames93 on 2012-07-01
Sorry i dont know what you mean , im new to ubuntu.

---

### Post by critin on 2012-07-01
> **Cjames93 said:**
> Sorry i dont know what you mean , im new to ubuntu.

When you post NEW REPLY there is a menu at the top for Bold, quotes, etc.                                                     
                                                                                             [COLOR=#000000][IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG][/COLOR]
                                                  
The hash mark  ----#----- is what you want.  Be sure the text is inside of those.

---

### Post by Cjames93 on 2012-07-01
```
Ubuntu Architecture  Linux DJames 2.6.32-41-generic #91-Ubuntu SMP Wed Jun 13 11:44:43 UTC 2012 i686 GNU/Linux  Ubuntu Version  DISTRIB_ID=Ubuntu DISTRIB_RELEASE=10.04 DISTRIB_CODENAME=lucid DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"  Firefox Packages  firefox						install firefox-branding				install firefox-gnome-support				install firefox-locale-en				install  Firefox binaries  /usr/bin/firefox /usr/bin/firefox: symbolic link to `../lib/firefox/firefox.sh' /usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory) /opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)  Firefox divertion  /usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)  Sources  google-chrome.list  Flash packages  Plugin locations   /usr/lib/mozilla/plugins/flashplugin-alternative.so  Flash symlinks   /usr/lib/mozilla/plugins/libflashplayer.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped /usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory) /etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory) /usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory) /usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory) /usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory) /usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory) /usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory) /usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory) /var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory) /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)  pluginreg.dat  Generated File. Do not edit.  [HEADER] Version:0.15:$ Arch:x86-gcc3:$  [PLUGINS] libflashplayer.so:$ /usr/lib/mozilla/plugins/libflashplayer.so:$ :$ 1336714805000:0:1:$ Shockwave Flash 11.2 r202:$ Shockwave Flash:$ 2 0:application/x-shockwave-flash:Shockwave Flash:swf:$ 1:application/futuresplash:FutureSplash Player:spl:$ IcedTeaPlugin.so:$ /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:$ :$ 1329507418000:0:5:$ The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-0ubuntu1~10.04.1)) executes Java applets.:$ IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-0ubuntu1~10.04.1)):$ 34 0:application/x-java-vm:IcedTea:class,jar:$ 1:application/x-java-applet:IcedTea:class,jar:$ 2:application/x-java-applet;version=1.1:IcedTea:class,jar:$ 3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$ 4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$ 5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$ 6:application/x-java-applet;version=1.2:IcedTea:class,jar:$ 7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$ 8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$ 9:application/x-java-applet;version=1.3:IcedTea:class,jar:$ 10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$ 11:application/x-java-applet;version=1.4:IcedTea:class,jar:$ 12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$ 13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$ 14:application/x-java-applet;version=1.5:IcedTea:class,jar:$ 15:application/x-java-applet;version=1.6:IcedTea:class,jar:$ 16:application/x-java-applet;jpi-version=1.6.0_20:IcedTea:class,jar:$ 17:application/x-java-bean:IcedTea:class,jar:$ 18:application/x-java-bean;version=1.1:IcedTea:class,jar:$ 19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$ 20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$ 21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$ 22:application/x-java-bean;version=1.2:IcedTea:class,jar:$ 23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$ 24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$ 25:application/x-java-bean;version=1.3:IcedTea:class,jar:$ 26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$ 27:application/x-java-bean;version=1.4:IcedTea:class,jar:$ 28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$ 29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$ 30:application/x-java-bean;version=1.5:IcedTea:class,jar:$ 31:application/x-java-bean;version=1.6:IcedTea:class,jar:$ 32:application/x-java-bean;jpi-version=1.6.0_20:IcedTea:class,jar:$ 33:application/x-java-vm-npruntime:::$ librhythmbox-itms-detection-plugin.so:$ /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$ :$ 1277463660000:0:5:$ This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$ iTunes Application Detector:$ 1 0:application/itunes-plugin:::$ libtotem-mully-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$ :$ 1274279893000:0:5:$ DivX Web Player version 1.4.0.233:$ DivXÂ® Web Player:$ 1 0:video/divx:AVI video:divx:$ libtotem-narrowspace-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$ :$ 1274279893000:0:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$ QuickTime Plug-in 7.6.6:$ 5 0:video/quicktime:QuickTime video:mov:$ 1:video/mp4:MPEG-4 video:mp4:$ 2:image/x-macpaint:MacPaint Bitmap image:pntg:$ 3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$ 4:video/x-m4v:MPEG-4 video:m4v:$ libtotem-cone-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$ :$ 1274279893000:0:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$ VLC Multimedia Plugin (compatible Totem 2.30.2):$ 19 0:application/x-vlc-plugin:VLC Multimedia Plugin::$ 1:application/vlc:VLC Multimedia Plugin::$ 2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$ 3:application/x-ogg:Ogg multimedia file:ogg:$ 4:application/ogg:Ogg multimedia file:ogg:$ 5:audio/ogg:Ogg Audio:oga:$ 6:audio/x-ogg:Ogg Audio:ogg:$ 7:video/ogg:Ogg Video:ogv:$ 8:video/x-ogg:Ogg Video:ogg:$ 9:application/annodex:Annodex exchange format:anx:$ 10:audio/annodex:Annodex Audio:axa:$ 11:video/annodex:Annodex Video:axv:$ 12:video/mpeg:MPEG video:mpg, mpeg, mpe:$ 13:audio/wav:WAV audio:wav:$ 14:audio/x-wav:WAV audio:wav:$ 15:audio/mpeg:MP3 audio:mp3:$ 16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$ 17:video/flv:Flash video:flv:$ 18:application/x-totem-plugin:Totem Multimedia plugin::$ libtotem-gmp-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$ :$ 1274279893000:0:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$ Windows Media Player Plug-in 10 (compatible; Totem):$ 13 0:application/x-mplayer2:AVI video:avi, wma, wmv:$ 1:video/x-ms-asf-plugin:ASF video:asf, wmv:$ 2:video/x-msvideo:AVI video:asf, wmv:$ 3:video/x-ms-asf:ASF video:asf:$ 4:video/x-ms-wmv:Windows Media video:wmv:$ 5:video/x-wmv:Windows Media video:wmv:$ 6:video/x-ms-wvx:Windows Media video:wmv:$ 7:video/x-ms-wm:Windows Media video:wmv:$ 8:video/x-ms-wmp:Windows Media video:wmv:$ 9:application/x-ms-wms:Windows Media video:wms:$ 10:application/x-ms-wmp:Windows Media video:wmp:$ 11:application/asx:Microsoft ASX playlist:asx:$ 12:audio/x-ms-wma:Windows Media audio:wma:$  [INVALID]
```

---

### Post by Cjames93 on 2012-07-01
Thanks, i think i did it right that time?

---

### Post by lovinglinux on 2012-07-01
I don't see anything wrong in your report. Flash is installed now and is detected by the browser. 

Try to disable hardware acceleration, delete the cache and delete cookies.

When you say it doesn't work, what exactly happens? What happens when you try to watch an YouTube video?

---

### Post by elliotn on 2012-07-01
maybe he mean a flv video....what did u try to okay, go to YouTube and play a video and post what happened

---

### Post by Cjames93 on 2012-07-02
when i click on you tube videos , everything loads apart from where the video is meant to so instead of the video playing its just a white background (it just blends into the you tube backgrounds white-ish colour. 
I dont know how to delete cookies for cache or disable hardware accelleration, im used to windows vista + Google chrome . sorry for all the hassle.

---

### Post by Cjames93 on 2012-07-02
I've added a screen shot of Youtube in the attachments if that helps?

---

### Post by Cjames93 on 2012-07-03
I cleared cache and cookies but i cant disable hardware acceleration because of flash not loading at all.

---

### Post by Cjames93 on 2012-07-03
Managed to disable hardware acceleration but still have the same issues, any ideas?

---

### Post by dino99 on 2012-07-03
flash support is dropped by adobe on linux, that it. So forget url using the latest flash.

---

### Post by lovinglinux on 2012-07-03
> **Cjames93 said:**
> when i click on you tube videos , everything loads apart from where the video is meant to so instead of the video playing its just a white background (it just blends into the you tube backgrounds white-ish colour. 
I dont know how to delete cookies for cache or disable hardware accelleration, im used to windows vista + Google chrome . sorry for all the hassle.

If you are used to Windows and Google Chrome, then install Chrome for Linux. It comes with the new PepperFlash that will be the only supported flash build for Linux.

[https://www.google.com/chrome/](https://www.google.com/chrome/)

There is a bug that is affecting some systems with old CPU, that prevents Chrome from starting. If you are affected by this, then see [http://ubuntuforums.org/showthread.php?t=2011882](http://ubuntuforums.org/showthread.php?t=2011882)

---

