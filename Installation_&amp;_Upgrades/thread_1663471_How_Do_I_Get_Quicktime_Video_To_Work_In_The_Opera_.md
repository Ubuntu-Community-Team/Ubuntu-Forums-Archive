---
title: "How Do I Get Quicktime Video To Work In The Opera Broswer?"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by Smallwheels on 2011-01-09
I downloaded some code that got Quicktime working in Firefox. It also got my VLC player and the Movie Player working. 

If I go to a quicktime video on the Apple.com web site it just shows the Quicktime logo and a message about how to get Quicktime for free with two buttons. One is for PC and the other is for Mac. 

What needs to be done to get Quicktime video playing on Opera using Ubuntu?

I can't find it on the Opera Forum. Also how does one find out which version of Opera is on the computer? I can't find it anywhere.

Thank you.

---

### Post by Frogs Hair on 2011-01-09
To find out what version Opera , you can go to Help > About. I have Quicktime installed , but I think it may have come as part of my Gstreamer Plugins and it shows up in my fire fox plugin list . Give me a link to a site that uses it and I will test it out on Opera.

---

### Post by Frogs Hair on 2011-01-09
I found a Quicktime test page and it seems to be working fine in Opera. I am using Opera 11.

---

### Post by Smallwheels on 2011-01-10
I wish I knew which version of Opera I had. 

A page to view a Quicktime video would be any on the Apple.com web site. The one I found was on the new Mac Book Air page. There were two videos there. 

My web browsers have been slow using Ubuntu compared to Vista's Firefox. I just wanted to know how to get videos to work on Opera right now. 

On Youtube now, when I open a video the video portion is black with a huge play button on it. If I move the cursor over it there is a message saying to click to activate this control. What is going on there? At least those videos work. 

What do I need to do to get Opera to play Quicktime videos? 

Thank you for your help.

---

### Post by Frogs Hair on 2011-01-10
When it offers to activate the control click it . I suggest you add the Ubuntu restricted extras from the software center. They include plugins for audio and video. To find tour current version of opera see the screen shots.

---

### Post by Smallwheels on 2011-02-10
It's been a while and I'm back on my Linux OS today. 

With the new information, I checked which version I have and it is 11.01. Today I went to the Apple.com site and went to the Mac page because I knew there would be a video there. I tried to play it and the player window opened with the Quicktime symbol telling me how to get Quicktime for Windows or Mac. No mention of Linux. 

Here is what I've done since visiting weeks ago. I updated Opera to the latest version. I also downloaded the Google Chromium browser. 

The results were great. Opera now operates at a quick speed comparable to my Mac Book browsers. Sometimes faster. Chromium is even faster. It will play the videos on the Apple.com web site and play them quickly, but; the video quality is very low. I mean it is almost blurry it is so bad. There are no video controls within Chromium. I can't pause the video or even see a progress bar. 

Firefox is still dead slow. Perhaps when I update it to the next stable version it will reconfigure itself the way Opera did and it will run fast as it is supposed to run. 

I would still like to get Quicktime videos playing within the Opera browser. I need help doing that on this Linux computer. 

There is no way I will choose Chromium as my primary browser unless I can fix that low quality video playback of Quicktime videos. The same goes for Firefox. It will play videos on the Apple.com web site with the same low quality. It is a bit better than Chromium because it adds video controls to the bottom of the video screen. The downside is that it will not play the video without stopping and resetting itself. Videos need to be paused and buffered in order to play them without hesitation. At least Chromium will play it all the way through without stopping. 

About the Ubuntu Software Center, which one will have the correct plug-in? What are the restricted extras? I didn't see that yet. Perhaps I haven't looked in the right spot. Could somebody tell me in which section to find them?

Thank you.

---

### Post by Smallwheels on 2011-03-24
I'm still hoping for an answer to this one folks. Adding the Ubuntu Restricted Extras did not work. 

Yesterday I got Firefox 4 working and it is running at the normal speed expected of a browser using a DSL connection. 

Now I need to know how to get Opera to play Quicktime videos. 

I tried using Chrome as my main browser on three OSs just because it could synchronize bookmarks across different computers. Chrome failed at doing that. It only syncs bookmarks not inside folders. Anything inside a bookmark folder was not transferred. Maybe Opera can succeed at that.

---

### Post by Smallwheels on 2011-03-31
Anybody? I suppose I'll just keep bumping this upward until the right person who can answer this responds. 

The question is how do I get Quicktime working within the Opera browser? The Ubuntu restricted extras did not succeed.

---

### Post by Old_Grey_Wolf on 2011-03-31
```

```> **Smallwheels said:**
> Anybody? I suppose I'll just keep bumping this upward until the right person who can answer this responds. 

The question is how do I get Quicktime working within the Opera browser? The Ubuntu restricted extras did not succeed.

I don't normally suggest executing a command without knowing what it does; however, I am not going to explain this one. Try installing all of the codecs and such with this command. It is for Ubuntu 10.04.
```
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-fluendo-mp3 gstreamer0.10-gnonlin gstreamer0.10-sdl gstreamer-dbus-media-service gstreamer-tools freepats gstreamer0.10-gnomevfs liba52-0.7.4 libavcodec52 libavformat52 libavutil49 libcdaudio1 libdc1394-22 libdca0 libdvdnav4 libdvdread4 libenca0 libfaac0 libfftw3-3 libfreebob0 libgsm1 libid3tag0 libiptcdata0 libkate1 libmad0 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0 libmpcdec3 libmpeg2-4 libofa0 libopenspc0 libpostproc51 libquicktime1 libschroedinger-1.0-0 libsidplay1 libsoundtouch1c2 libswscale0 libtwolame0 libwildmidi0 libxml++2.6-2 libxvidcore4 w32codecs libdvdcss2 libxine1-ffmpeg debhelper fakeroot libfftw3-dev sidplay-base liblrdf0-dev xsidplay mplayer avifile-divx-plugin avifile-xvid-plugin dh-make g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg cvs gettext-doc avifile-mad-plugin avifile-mjpeg-plugin avifile-player avifile-utils avifile-vorbis-plugin avifile-win32-plugin libcurl3-dbg libgcrypt11-doc libggi-target-emu libggi-target-monotext libggimisc2 gnutls-doc gnutls-bin guile-gnutls krb5-doc libraptor1-doc libstdc++6-4.3-doc mplayer-doc diff-doc easytag-aac faac faad ffmpeg ffmpeg2theora flac icedax id3tool id3v2 lame liba52-0.7.4-dev libavfilter0 libflac++6 libid3-3.8.3c2a libjpeg-progs libmp4v2-0 libmpg123-0 libsox-fmt-alsa libsox-fmt-base libsox1a mpeg2dec mpeg3-utils mpegdemux mpg123 mpg321 sox tagtool twolame vorbis-tools build-essential comerr-dev cpp-4.3 dpkg-dev g++ g++-4.3 g++-4.4 g++-4.4-multilib gcc-4.3 gcc-4.3-base gcc-4.3-multilib gcc-4.4-multilib gcc-multilib gettext gnome-mplayer guile-1.8 html2text intltool-debian ladspa-sdk lib64gcc1 lib64gomp1 lib64stdc++6 libao2 libaudio2 libavdevice52 libavifile-0.7c2 libc6-amd64 libc6-dev-amd64 libcurl4-gnutls-dev libdiscid0 libgcc1-dbg libgcrypt11-dev libggi-target-terminfo libggi-target-x libggi2 libgii1 libgii1-target-x libgnutls-dev libgpg-error-dev libgssrpc4 libidn11-dev libkdb5-4 libkrb5-dev libldap2-dev liblrdf0 liblzo2-2 libmail-sendmail-perl libmpeg3-1 libmusicbrainz3-6 libopenal1 libqt3-mt libqt4-xml libqtcore4 libqtgui4 libraptor1-dev libreadline5 libstdc++6-4.3-dev libstdc++6-4.4-dev libsvga1 libsys-hostname-long-perl libtasn1-3-dev libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxml2-dev libxslt1-dev mplayer-nogui mplayer-skins patch po-debconf zlib1g-dev libdvbpsi5 libebml0 liblua5.1-0 libmatroska0 libsdl-image1.2 jack-tools jackd libjackasyn0 qjackctl libjack0 libdirac-encoder0 libdirac-decoder0 cpp-4.3 diffutils-doc gecko-mediaplayer krb5-multidev libffado2 libkadm5clnt-mit7 libkadm5srv-mit7 raptor-utils jackd-firewire

```

For Ubuntu 10.10 use this command.
```
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-gnonlin freepats gstreamer-dbus-media-service gstreamer-tools gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-gnomevfs gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-sdl liba52-0.7.4 libass4 libavformat52 libcdaudio1 libcelt0-0 libdc1394-22 libdca0 libdirac-encoder0 libdirectfb-1.2-9 libdvdnav4 libdvdread4 libenca0 libfaac0 libfaad2 libfftw3-3 libflite1 libgme0 libgsm1 libid3tag0 libiptcdata0 libkate1 libmad0 libmimic0 libmjpegtools-1.9 libmms0 libmodplug1 libmp3lame0 libmpcdec6 libmpeg2-4 libofa0 liboil0.3 libopencore-amrnb0 libopencore-amrwb0 libopenspc0 libpostproc51 libquicktime1 librtmp0 libschroedinger-1.0-0 libsidplay1 libsoundtouch1c2 libts-0.0-0 libtwolame0 libva1 libvpx0 libwildmidi0 libx264-98 libxvidcore4 libzbar0 tsconf w32codecs libdvdcss2 debhelper build-essential libfftw3-dev sidplay-base xsidplay dpkg-dev esound-clients esound-common g++ g++-4.4 gettext html2text intltool-debian libalgorithm-diff-perl libalgorithm-merge-perl libaudio2 libaudiofile0 libdpkg-perl libesd0 libmail-sendmail-perl libmng1 libqt3-mt libstdc++6-4.4-dev libsys-hostname-long-perl libunistring0 po-debconf dh-make debian-keyring g++-multilib g++-4.4-multilib gcc-4.4-doc libstdc++6-4.4-dbg gettext-doc nas libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc libstdc++6-4.4-doc gcc-4.4-multilib gcc-multilib lib64gcc1 lib64gomp1 lib64stdc++6 libc6-amd64 libc6-dev-amd64 libgcc1-dbg libiodbc2 libmysqlclient16 libpq5 mysql-common lib64mudflap0 audiooss mplayer mplayer-doc apport-hooks-medibuntu avifile-divx-plugin avifile-mad-plugin avifile-mjpeg-plugin avifile-player avifile-utils avifile-vorbis-plugin avifile-win32-plugin avifile-xvid-plugin cpp-4.3 cvs diff-doc diffutils-doc easytag-aac faac faad ffmpeg ffmpeg2theora flac g++-4.3 g++-4.3-multilib gcc-4.3 gcc-4.3-base gcc-4.3-doc gcc-4.3-multilib gnutls-bin gnutls-doc guile-1.8 guile-gnutls icedax libavdevice52 libavifile-0.7c2 libcurl3-dbg libgcrypt11-doc libggi-target-emu libggi-target-monotext libggi-target-terminfo libggi-target-x libggi2 libggimisc2 libgif4 libgii1 libgii1-target-x liblzo2-2 libmp4v2-0 libopenal1 libraptor1-doc libstdc++6-4.3-dev libsvga1 libvdpau1 gcc-4.3-locales lib64stdc++6-4.4-dbg libmudflap0-4.3-dev libgomp1-dbg libmudflap0-dbg guile-1.8-doc vorbis-tools cdrkit-doc libgcrypt11-dev libao-common libao4 libc6-dbg libgpg-error-dev libmudflap0 fping comerr-dev gecko-mediaplayer gnome-mplayer id3tool id3v2 ladspa-sdk lame liba52-0.7.4-dev libavcodec-extra-52 libavfilter-extra-1 libavutil-extra-50 libcurl4-gnutls-dev libdirac-decoder0 libdiscid0 libdvbpsi5 libffado2 libflac++6 libgnutls-dev libgssrpc4 libid3-3.8.3c2a libidn11-dev libjpeg-progs libjpeg8 libkadm5clnt-mit7 libkadm5srv-mit7 libkdb5-4 libldap2-dev liblrdf0 libmpeg3-1 libmpg123-0 libmusicbrainz3-6 libopenjpeg2 libraptor1-dev libreadline5 libsox-fmt-alsa libsox-fmt-base libsox1b libswscale-extra-0 libtasn1-3-dev libxcb-shape0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxml++2.6-2 libxml2-dev libxslt1-dev mpeg2dec mpeg3-utils mpegdemux mpg123 mpg321 mplayer-skins raptor-utils sox tagtool twolame zlib1g-dev liblrdf0-dev libsox-fmt-all gxine xine-ui libxine1-doc libxine1-ffmpeg libsox-fmt-ao libsox-fmt-ffmpeg libsox-fmt-mp3 libsox-fmt-oss libsox-fmt-pulse krb5-multidev lib64gcc1-dbg libkrb5-dev libxcb-xv0
```

---

