---
title: "Mplayer in Firefox not working"
date: 2005-06-20
forum: Installation &amp; Upgrades
---

### Post by drdeutsch on 2005-06-20
I added the extra repositories, installed codecs and DVD playback support, and installed MPlayer and Plugins for Firefox per ubuntuguide.org. Everything updated correctly, absolutely no error messages whatsoever.

However, whenever I click on a file to be streamed in firefox, mplayer will load up in the window and start buffering. When it gets to about 25% buffered, it'll go black, but firefox will continue to load the page. Then... nothing happens.  I'm left with a firefox page with a black space where mplayer should be playing the file.

Any ideas?
thanks,
drdeutsch

---

### Post by Skel on 2005-06-24
I get the same thing.. Searching forums for answer at the moment

---

### Post by soypablo on 2005-06-24
[QUOTE=drdeutsch]I added the extra repositories, installed codecs and DVD playback support, and installed MPlayer and Plugins for Firefox per ubuntuguide.org. Everything updated correctly, absolutely no error messages whatsoever.

However, whenever I click on a file to be streamed in firefox, mplayer will load up in the window and start buffering. When it gets to about 25% buffered, it'll go black, but firefox will continue to load the page. Then... nothing happens.  I'm left with a firefox page with a black space where mplayer should be playing the file.

Any ideas?
thanks,
drdeutsch[/QUOTE]
 You need to edit /etc/mplayerplug-in.conf, uncommenting lines as appropriate.  Here's mine:

#debug=0
#logfile=$HOME/mpp.log
vo=xv,x11
ao=alsa,esd,oss
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
noembed=1
#cachesize=256
use-mimetypes=1
enable-real=0
enable-wm=1
enable-qt=1
#enable-mpeg=1
#enable-ogg=1
qt-speed=high
#rtsp-use-tcp=0
#nomediacache=0

After doing that, delete the pluginreg.dat files in your .mozilla and .mozilla/firefox directories.  Restart Firefox and you should be in business.

---

### Post by crashtest on 2005-06-24
[QUOTE=soypablo]You need to edit /etc/mplayerplug-in.conf, uncommenting lines as appropriate.  Here's mine:

#debug=0
#logfile=$HOME/mpp.log
vo=xv,x11
ao=alsa,esd,oss
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
noembed=1
#cachesize=256
use-mimetypes=1
enable-real=0
enable-wm=1
enable-qt=1
#enable-mpeg=1
#enable-ogg=1
qt-speed=high
#rtsp-use-tcp=0
#nomediacache=0

After doing that, delete the pluginreg.dat files in your .mozilla and .mozilla/firefox directories.  Restart Firefox and you should be in business.[/QUOTE]

I tried this, and mplayer opens, then pops up 3 Fatal error! boxes, one after the other.

1.  MPlayer interrupted by signal 11 in module: demux_open

2. MPlayer crashed by bad usage of CPU/FPU/RAM.  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and disassembly.

3. MPlayer crashed.  This shouldn't happen.  It can be a bug in the MPlayer core _or_ in your drivers _or_ in your gcc version.

Any tips would be appreciated.  Reading the forums I see a lot of people with problems running mplayer in Firefox - and a lot more who say "works for me"

Like the original poster, I have followed all the steps in ubuntuguide.org.

---

### Post by Skel on 2005-06-24
I got the very same thign when i did all that just comes up with a pop up 
 :? 

Maybe someone has a magic wond that will fix it :wink:

---

### Post by Dave_is_sexy on 2005-06-24
Yep me too. But i thought it was ugly anyway so installed the VLC one (via synaptic - just use edit > search) and it looks way better and works perfectly.

You hav eto navigate to /usr/share/mozilla-firefox/plugins and delete the mplayer one.

...that's unless you especially want to have mplayer handle everything for some reason, but i prefer the VLC one anyday

---

### Post by wylfing on 2005-06-24
Does VLC handle Windows Media? That's the only reason I have mplayer.

To those with mplayer not behaving itself and/or crashing: is OpenGL working on your system? I've found that mplayer will crash if OpenGL is not functioning. In Firefox this looks like the plugin is just sitting there doing nothing. Try running 'glxgears' and see what happens.

---

### Post by Skel on 2005-06-24
I have installed VLC and i can now watch Streaming movie..WOOT  :razz:  but i cant listen to the audio ](*,) anyone know a fix for this

---

### Post by WAM on 2005-06-25
[QUOTE=Skel]I have installed VLC and i can now watch Streaming movie..WOOT  :razz:  but i cant listen to the audio ](*,) anyone know a fix for this[/QUOTE]
 Skel, try this.

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.l

---

### Post by Dave_is_sexy on 2005-06-25
Oh. My VLC plugin has stopped working. That's random. Anyone got a fix for mplayer yet?

---

