---
title: "Better Luck Second Time?"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by JohnMorrow on 2008-02-18
Some months ago I installed Fiesty (7.04) on my HP Pavilion desktop. Never could get Flash to work properly and the printer stopped working (CUPS) after a few weeks, no idea why. I also have some sound issues (pulsing) and Firefox once in a while spontaneously closes. Time to punt.

So I have downloaded,  burned and tested the 7.10 CD (AMD 64 flavor for my AMD Athlon 64 X2 Dual Core processor), I have backed up my data and am ready to re-partition and try again. I intend to keep Win XP and 7.04 in a multi-boot setup.

First order of business will be to get the on-board nVidia GeForce 6150 drivers installed.

Then to get the Brother MFC-440-CN network printer running.

Then to install Java.

Then to install Flash.

Then to install other multimedia players and codecs.

So the first time around I used "Easy Ubuntu" to add in the mulitmedia stuff that is not included in the distribution. Easy Ubuntu is no longer supported.

In Daniel Andrade's blog, 
[http://www.danielandrade.net/2007/11/10/10-things-to-do-just-after-installing-ubuntu-710/](http://www.danielandrade.net/2007/11/10/10-things-to-do-just-after-installing-ubuntu-710/)

a user recommended installing Automatix 
[http://www.getautomatic.com](http://www.getautomatic.com)         but another user said it breaks things. Who to believe?

Any recommendations on

1. installing and troubleshooting printers?

2. installing Flash on an AMD 64 (should I use the 32 bit version?)

3. A simple GUI method for installing multimedia support and players?

Thanks!
John

---

### Post by Pumalite on 2008-02-18
No 3:
sudo aptitude install ubuntu-restricted-extras

---

### Post by Helios89 on 2008-02-18
well, in my opinion it would be better if you installed the 32-bit version, because the 64-bit one, afaik, is less stable. I had almost no problem with the 32-bit version on my 64-bit box. :)

---

### Post by JohnMorrow on 2008-02-18
Thank you for your replies.

The installation went smoothly for the most part. The nVidia drivers are installed and active. Seems like a ton of stuff is installed with the default configuration, so I will need to explore and see what I have. Update Manager says 186 updates are available (239 MB worth); I will go ahead and install all of them.

 I agree, the 32-bit version of Flash may end up being more stable and reliable.

John

---

### Post by JohnMorrow on 2008-02-18
Pumalite:

I opened a terminal window and used the command you suggested:

sudo aptitude install ubuntu-restricted-extras 

and at first it seemed to go well. All packages downloaded and about the first six installed fine. The procedure choked during the Java install, when a colored text box appeared with a long License agreement from Sun. It appeared that I had to acknowledge the agreement because the characters <OK> were at the bottom of the box. I hit the <Enter> key (repeatedly) to no effect. I copied the terminal window messages that were still accessible into a text document, then closed the window. I assume I will have to open a new terminal window and try again. 

The Terminal window messages are below; comments are welcome.

john@HP-desktop:~$ sudo aptitude install ubuntu-restricted-extras
[sudo] password for john:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  cabextract gcc-3.3-base gsfonts-x11 jackd java-common liba52-0.7.4 
  libaudio2 libavcodec1d libavutil1d libcdaudio1 libdvdread3 libfaac0 
  libfaad2-0 libfreebob0 libgsm1 libid3tag0 libjack0 liblame0 libmad0 
  libmjpegtools0c2a libmms0 libmp4v2-0 libmpcdec3 libmpeg2-4 libqt3-mt 
  libquicktime1 libsidplay1 libsoundtouch1c2 libstdc++5 libx264-54 
  libxvidcore4 odbcinst1debian1 qjackctl sun-java6-bin unixodbc 
The following NEW packages will be installed:
  cabextract gcc-3.3-base gsfonts-x11 gstreamer0.10-ffmpeg 
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse 
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse jackd 
  java-common liba52-0.7.4 libaudio2 libavcodec1d libavutil1d libcdaudio1 
  libdvdread3 libfaac0 libfaad2-0 libfreebob0 libgsm1 libid3tag0 libjack0 
  liblame0 libmad0 libmjpegtools0c2a libmms0 libmp4v2-0 libmpcdec3 
  libmpeg2-4 libqt3-mt libquicktime1 libsidplay1 libsoundtouch1c2 
  libstdc++5 libx264-54 libxvidcore4 msttcorefonts odbcinst1debian1 
  qjackctl sun-java6-bin sun-java6-jre ubuntu-restricted-extras unixodbc 
  unrar 
0 packages upgraded, 44 newly installed, 0 to remove and 0 not upgraded.
Need to get 43.0MB of archives. After unpacking 122MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main java-common 0.26ubuntu1 [77.1kB]

<CUT - screen overwritten by Sun license agreement>

Unpacking gcc-3.3-base (from .../gcc-3.3-base_1%3a3.3.6-15ubuntu2_amd64.deb) ...
Selecting previously deselected package libstdc++5.
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-15ubuntu2_amd64.deb) ...
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6-03-0ubuntu2_amd64.deb) ...

---

### Post by JohnMorrow on 2008-02-18
UPDATE:

FYI, I tried to open Synaptic Package Manager and got the following error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I did as told:

john@HP-desktop:~$ sudo dpkg --configure -a
[sudo] password for john:
Setting up java-common (0.26ubuntu1) ...

Setting up odbcinst1debian1 (2.2.11-16) ...

Setting up unixodbc (2.2.11-16) ...

Setting up gcc-3.3-base (1:3.3.6-15ubuntu2) ...
Setting up libstdc++5 (1:3.3.6-15ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
john@HP-desktop:~$ 


More to come...

---

### Post by Partyboi2 on 2008-02-19
> The procedure choked during the Java install, when a colored text box appeared with a long License agreement from Sun. It appeared that I had to acknowledge the agreement because the characters <OK> were at the bottom of the box. I hit the <Enter> key (repeatedly) to no effect.
did you hit the tab key first so that the word ok was highlighted  before pressing enter?

---

### Post by JohnMorrow on 2008-02-19
Partyboi2:

No, on the first attempt I didn't use the tab key, but next time I did, and Sun Java6 installed fine. Unfortunately, about:plugins showed no Java plugin.

According to the site below, Sun doesn't yet make a plugin for AMD64.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
 "As of 2007-01-19, there is only one plugin that works and that is the one included with Blackdown Java 1.4.2."

So I have installed Blackdown, but still no Java plugins showing up in about:plugins.

---

### Post by Partyboi2 on 2008-02-19
you could try [this]("http://sudan.ubuntuforums.com/showthread.php?t=202537")

---

### Post by JohnMorrow on 2008-02-19
Partyboi2:

Thanks a million, "Kilz's" script worked like a charm!

I also looked at

[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

[http://www.mutaku.com/geeklog/article.php?story=20080116181440588](http://www.mutaku.com/geeklog/article.php?story=20080116181440588)

[http://wiki.serios.net/wiki/Debian_Java_JRE/JDK_installation%2C_browser_plugin](http://wiki.serios.net/wiki/Debian_Java_JRE/JDK_installation%2C_browser_plugin)

[http://www.linuxquestions.org/questions/debian-26/browser-support-for-java-shockwave-and-flash-with-amd64-621157/#post3062101](http://www.linuxquestions.org/questions/debian-26/browser-support-for-java-shockwave-and-flash-with-amd64-621157/#post3062101)

but in the end they were too much hassle. Your link was best. Thanks again!

John

---

### Post by JohnMorrow on 2008-02-19
Hello again:

Updated Firefox32 from 2.0.0.11 to 2.0.0.12 and all plugins disappeared from about:plugins, although the files are still in /usr/lib32/firefox32/plugins/

In Kilz's "Common Problems" area he appears to address this issue, with the advice below. I tried the command and it didn't work - I still have no working plugins.

COMMON PROBLEMS

If a plugin doesnt seem to work, and typing
Code:

about:plugins


in the address bar of the browser dose not list them try this making sure to replace USERNAME in the following command with the name you use to login with.

Code:

sudo chown -hR USERNAME:users /usr/lib32/firefox32/plugins

<break>

Q: Can you run the 64-bit and 32-bit versions of Firefox at the same time? I was running both when I upgraded the 32-bit version

---

