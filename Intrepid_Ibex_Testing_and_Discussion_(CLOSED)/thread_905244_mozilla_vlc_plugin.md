---
title: "mozilla vlc plugin"
date: 2008-08-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Predrag on 2008-08-30
Hi I have a problem with vlc plugin.When I play some film in mozilla I have problem with another window.When I click on this window my mozilla is crashing down.there is some video [http://linuxsoftware.tym.sk/out.ogv](http://linuxsoftware.tym.sk/out.ogv) .im using Ubuntu 8.10 alpha4.Nvidia 7600gs.


predrag@predrag:~$ firefox
/usr/bin/apturl:278: GtkWarning: gtk_widget_grab_default: assertion `GTK_WIDGET_CAN_DEFAULT (widget)' failed
  'confirmation_dialog')
predrag@predrag:~$ firefox
argn=pluginspage, argv=http://www.videolan.org
argn=type, argv=application/x-vlc-plugin
argn=progid, argv=VideoLAN.VLCPlugin.2
argn=loop, argv=true
argn=name, argv=vlc
argn=width, argv=640
argn=height, argv=480
[00000001] main private debug: checking builtin modules
[00000001] main private debug: checking plugin modules
[00000001] main private debug: loading plugins cache file /home/predrag/.vlc/cache/plugins-04041e.dat
[00000001] main private debug: recursively browsing `/usr/lib/vlc'
[00000001] main private debug: module bank initialized, found 218 modules
[00000001] main private debug: opening config file /home/predrag/.vlc/vlcrc
[00000001] main private warning: config file /home/predrag/.vlc/vlcrc does not exist yet
[00000001] main private debug: CPU has capabilities 486 586 MMX 3DNow! MMXEXT SSE SSE2 FPU 
[00000001] main private debug: looking for memcpy module: 1 candidate
[00000001] main private debug: using memcpy module "memcpy"
[00000283] main playlist debug: waiting for thread completion
[00000283] main playlist debug: thread 2976107408 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000284] main private debug: waiting for thread completion
[00000284] main private debug: thread 2967714704 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000285] main interface debug: looking for interface module: 1 candidate
[00000285] main interface debug: using interface module "hotkeys"
[00000285] main interface debug: thread 2959293328 (interface) created at priority 0 (interface/interface.c:231)
[00000287] main interface debug: looking for interface module: 1 candidate
[00000287] main interface debug: using interface module "screensaver"
[00000287] main interface debug: thread 2950888336 (interface) created at priority 0 (interface/interface.c:231)
[00000001] main private debug: removing all interfaces
[00000287] main interface debug: thread 2950888336 joined (interface/interface.c:258)
[00000287] main interface debug: removing module "screensaver"
[00000285] main interface debug: thread 2959293328 joined (interface/interface.c:258)
[00000285] main interface debug: removing module "hotkeys"
[00000001] main private debug: removing playlist handler
[00000284] main private debug: thread 2967714704 joined (playlist/playlist.c:247)
[00000283] main playlist debug: thread 2976107408 joined (playlist/playlist.c:248)
[00000001] main private debug: removing all video outputs
[00000001] main private debug: removing all audio outputs
[00000001] main private debug: removing module "memcpy"
[00000001] main private debug: saving plugins cache file /home/predrag/.vlc/cache/plugins-04041e.dat
argn=pluginspage, argv=http://www.videolan.org
argn=type, argv=application/x-vlc-plugin
argn=progid, argv=VideoLAN.VLCPlugin.2
argn=loop, argv=true
argn=name, argv=vlc
argn=width, argv=640
argn=height, argv=480
[00000001] main private debug: checking builtin modules
[00000001] main private debug: checking plugin modules
[00000001] main private debug: loading plugins cache file /home/predrag/.vlc/cache/plugins-04041e.dat
[00000001] main private debug: recursively browsing `/usr/lib/vlc'
[00000001] main private debug: module bank initialized, found 218 modules
[00000001] main private debug: opening config file /home/predrag/.vlc/vlcrc
[00000001] main private warning: config file /home/predrag/.vlc/vlcrc does not exist yet
[00000001] main private debug: CPU has capabilities 486 586 MMX 3DNow! MMXEXT SSE SSE2 FPU 
[00000001] main private debug: looking for memcpy module: 1 candidate
[00000001] main private debug: using memcpy module "memcpy"
[00000283] main playlist debug: waiting for thread completion
[00000283] main playlist debug: thread 2976107408 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000284] main private debug: waiting for thread completion
[00000284] main private debug: thread 2967714704 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000285] main interface debug: looking for interface module: 1 candidate
[00000285] main interface debug: using interface module "hotkeys"
[00000285] main interface debug: thread 2959293328 (interface) created at priority 0 (interface/interface.c:231)
[00000287] main interface debug: looking for interface module: 1 candidate
[00000287] main interface debug: using interface module "screensaver"
[00000287] main interface debug: thread 2950888336 (interface) created at priority 0 (interface/interface.c:231)
firefox: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

---

### Post by Predrag on 2008-09-14
nobody knows?

---

### Post by Nullack on 2008-09-14
Your using a non standard bit of software, so help will be thin on the ground.

Whats missing from the default install with gstreamer that you can do?

---

### Post by plun on 2008-09-14
> **Predrag said:**
> nobody knows?

Nope, but I checked your demo video.

I think this is a bug with the plugin finder and a vlc install

A correct install
```
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```

Works OK for me manually installed so please file a bug !

---

### Post by The Keeper on 2008-09-15
I believe vlc 0.8.6 browser plugin is known to be quite poor quality actually, so I wouldn't be surprised if you have problems with it. Supposedly "soon" to be released 0.9 should be quite an improvement over 0.8.6, I don't know as I haven't tried the betas.

I suggest you try mplayer and its browser plugin instead.

---

