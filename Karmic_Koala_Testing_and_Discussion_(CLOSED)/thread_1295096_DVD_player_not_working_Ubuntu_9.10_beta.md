---
title: "DVD player not working Ubuntu 9.10 beta"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 2blue on 2009-10-19
I just installed the beta version, and it's first time for ubuntu on this laptop. I am testing out applications and somehow DVD or CD player will not work. I have installed a package of restriced extras from synaptic and restricted drivers from a icon on the application menu. Any thing else I should do.  

It's probably not caused by any bug in the beta version, more likely a more or less ordinary configuration problem.

---

### Post by arochester on 2009-10-19
You need to install: Medibuntu Repository
and install the package: libdvdcss2

Instructions for Medubuntu here: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

NOTE. It is a 2 part installation 1) Install Repository 2) Get GPG key

---

### Post by mapes12 on 2009-10-19
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

and try a different media player e.g. VLC. It's in Synaptic.

---

### Post by 2blue on 2009-10-19
I have installed VLC and all restricted and unrestritced packages that I can find than seam relevant. Still DVD player will not work. 

There is some improvement, it plays CD's all right now, both VLC and Rhythmbox.  

I have been through all help pages I can find on the subject. Any suggestions? :confused:

---

### Post by swoody on 2009-10-20
Have you run all available updates? Is this an encrypted DVD you are trying to play?

You may want to read over this Multimedia How-To:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

After adding the Medibuntu repository you'll want to add these packages:
```
sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4
```

Try that out, and let us know how it works :)

---

### Post by desperado665 on 2009-10-20
> **swoody said:**
> After adding the Medibuntu repository you'll want to add these packages:
```
sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4
```

Then also run ```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by vinutux on 2009-10-20
> **desperado665 said:**
> then also run ```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

+1

---

### Post by 2blue on 2009-10-20
the "sudo apt-get install" command for the libdvd-packages didn't work, however the last command "sudo /usr/share/doc/libdvdread4/install-css.sh" did install. Still DVDs doesn't play. I have tried different DVDs, bought region 2 that should work, and other burned ones.  

I have to do some more search and reading. This is first time with Ubuntu on this laptop. I wonder if that might have something to do with it, or just some package still missing.

---

### Post by swoody on 2009-10-20
> **2blue said:**
> the "sudo apt-get install" command for the libdvd-packages didn't work

Can you give us the error output that it gave you? Also, have you checked that all your repositories (namely main and universe) are selected? And the Medibuntu repository installed without issue?

---

### Post by dalonso on 2009-10-20
Please, read my post here and tell us if it works for you. 

[http://ubuntuforums.org/showpost.php?p=8060778&postcount=5](http://ubuntuforums.org/showpost.php?p=8060778&postcount=5)

No need to enable Medibuntu. It just worked for me by installing additional gstreamer plugins from universe.

---

### Post by cor2y on 2009-10-20
A quick FYI totem will fail at dvd playback if you have the fluendo gstreamer plugins installed.
The latest fluendo 7.0 conflicts with gstreamer-plugins-bad so they cant be installed with fluendo and for dvd playback in totem (now that totem-xine is gone) you need gstreamer-plugins-bad.
So will have to do without the fluendo plugins for a while if you want dvd playback in totem.

---

### Post by 2blue on 2009-10-20
I would be happy if any DVD player working. I have Totem, VLC and Xine, and no-one is working. CD play well, and I have burned a Puppy-iso CD in Brasero with out any problem. I checked in Synaptics Package Manager, and I could not find any marked off fluendo-packages.

---

### Post by cariboo on 2009-10-20
After seeing this thread, I had to try playing a DVD. I get an error using vlc when opening the dvd from the file menu, but if I right click on the dvd icon on the desktop and select open with vlc, the dvd plays as it should. I tried 3 different dvd's and they all work the same way. One dvd was self creted, and the other two were commercial, The Mummy III and Wanted.

---

### Post by 2blue on 2009-10-20
Thanks for the tip, but I have played around with different options, opening from the desktop-icon too. I don't know what to think now, any thing wrong with my DVD rom? It is a while since I used, a couple of months or so, but it worked fine in Windows XP.

---

### Post by mc4man on 2009-10-20
> but I have played around with different options....

Assuming you're trying to play a dvd disc in drive

open vlc from terminal with this, then go media -> Open disc and see what happens. If vlc fails to open movie then close vlc and look in home folder for file vlc_output and see what if says.

```

vlc -vv > vlc_output 2>&1
```

Usually you can ignore the first 80 -90 lines, anything below this may prove relevant
> ....................................
[0x9614140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x96c1510] main interface debug: looking for interface module: 4 candidates
[0x96c1510] qt4 interface debug: Error while initializing qt-specific localization
[COLOR="Blue"][0x96c1510] main interface debug: using interface module "qt4"[/COLOR]


---

### Post by 2blue on 2009-10-21
This might be significant in figuring out the problem;

Ubuntu has difficulties recognising media when I'm putting in the dvd. It cannot mount DVDs very well, and I have to open the DVD rom and close it again a couple of time before any icon appears on the desktop, or leave it in for a very long time. 

DVD rom is very active when DVD is installed, I hear sounds an some kind of action but no recognition of media.

---

### Post by 2blue on 2009-10-21
I  just ran update manager and rebooted, now I get very clair messages that I am missing plugins, in both VLC and Xine. Movieplayer mounst DVD with some difficulties but are very jerky, not really a movie, more like random pictures, sound is fine. 

I shall have to cheks media-packages and try to install them over again?

---

### Post by 2blue on 2009-10-21
> **mc4man said:**
> Assuming you're trying to play a dvd disc in drive

open vlc from terminal with this, then go media -> Open disc and see what happens. If vlc fails to open movie then close vlc and look in home folder for file vlc_output and see what if says.

```

vlc -vv > vlc_output 2>&1
```

Usually you can ignore the first 80 -90 lines, anything below this may prove relevant


This almost works, DVD is mounted, it starts in VLC, I can see some pictures, but it dosen't play the film.

---

### Post by mc4man on 2009-10-21
> ...I can see some pictures, but it dosen't play the film.

Can you look in home folder at the file "vlc_output" and maybe post some of it.
( will be rather large, refer back to previous post and look at what's shown after line marked in blue - about 80 - 90 lines in.

---

### Post by 2blue on 2009-10-21
Thank you for your patience mc4man, I was a bit slow to get this one. I have tried all the suggestions and commands you guys have posted, it is appreciated. Here is the long list: 


```
VLC media player 1.0.2 Goldeneye
[0x84a5140] main libvlc debug: VLC media player - version 1.0.2 Goldeneye - (c) 1996-2009 the VideoLAN team
[0x84a5140] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--disable-maintainer-mode' '--enable-release' '--prefix=/usr' '--config-cache' '--enable-fast-install' '--with-binary-version=1ubuntu2' '--disable-update-check' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=xulrunner-plugin' '--enable-dvb' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--enable-flac' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-mod' '--enable-theora' '--enable-dvdnav' '--enable-gnutls' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-x264' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-dca' '--enable-realrtsp' '--disable-dv' '--disable-fluidsynth' '--disable-kate' '--disable-mtp' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x84a5140] main libvlc debug: translation test: code is "C"
[0x84a5140] main libvlc debug: checking plugin modules
[0x84a5140] main libvlc debug: loading plugins cache file /home/lovinguniverse/.cache/vlc/plugins-04041e.dat
[0x84a5140] main libvlc debug: recursively browsing `/usr/lib/vlc'
[0x84a5140] main libvlc debug: module bank initialized (375 modules)
[0x84a5140] main libvlc debug: opening config file (/home/lovinguniverse/.config/vlc/vlcrc)
[0x84a5140] main libvlc debug: CPU has capabilities 486 586 MMX MMXEXT FPU 
[0x84a5140] main libvlc debug: looking for memcpy module: 3 candidates
[0x84a5140] main libvlc debug: using memcpy module "memcpymmxext"
[0x85463b0] main input debug: Creating an input for 'Media Library'
[0x85463b0] main input debug: Input is a meta file: disabling unneeded options
[0x85463b0] main input debug: using timeshift granularity of 50 MBytes
[0x85463b0] main input debug: using timeshift path '/tmp'
[0x85463b0] main input debug: `file/xspf-open:///home/lovinguniverse/.local/share/vlc/ml.xspf' gives access `file' demux `xspf-open' path `/home/lovinguniverse/.local/share/vlc/ml.xspf'
[0x85463b0] main input debug: creating demux: access='file' demux='xspf-open' path='/home/lovinguniverse/.local/share/vlc/ml.xspf'
[0x853c448] main demux debug: looking for access_demux module: 1 candidate
[0x853c448] main demux warning: no access_demux module matching "file" could be loaded
[0x853c448] main demux debug: TIMER module_need() : 22.498 ms - Total 22.498 ms / 1 intvls (Avg 22.498 ms)
[0x85463b0] main input debug: creating access 'file' path='/home/lovinguniverse/.local/share/vlc/ml.xspf'
[0x853e210] main access debug: looking for access module: 3 candidates
[0x853e210] access_file access debug: opening file `/home/lovinguniverse/.local/share/vlc/ml.xspf'
[0x853e210] main access debug: using access module "access_file"
[0x853e210] main access debug: TIMER module_need() : 50.894 ms - Total 50.894 ms / 1 intvls (Avg 50.894 ms)
[0x853d778] main stream debug: Using AStream*Stream
[0x853d778] main stream debug: pre buffering
[0x853d778] main stream debug: received first data after 0 ms
[0x853d778] main stream debug: pre-buffering done 296 bytes in 0s - 986 kbytes/s
[0x853db88] main stream debug: looking for stream_filter module: 4 candidates
[0x853db88] main stream debug: TIMER module_need() : 25.931 ms - Total 25.931 ms / 1 intvls (Avg 25.931 ms)
[0x853db88] main stream debug: looking for stream_filter module: 1 candidate
[0x853db88] main stream debug: using stream_filter module "stream_filter_record"
[0x853db88] main stream debug: TIMER module_need() : 25.976 ms - Total 25.976 ms / 1 intvls (Avg 25.976 ms)
[0x85463b0] main input debug: creating demux: access='file' demux='xspf-open' path='/home/lovinguniverse/.local/share/vlc/ml.xspf'
[0x854d138] main demux debug: looking for demux module: 1 candidate
[0x854d138] playlist demux debug: using XSPF playlist reader
[0x854d138] main demux debug: using demux module "playlist"
[0x854d138] main demux debug: TIMER module_need() : 38.956 ms - Total 38.956 ms / 1 intvls (Avg 38.956 ms)
[0x85463b0] main input debug: `file/xspf-open:///home/lovinguniverse/.local/share/vlc/ml.xspf' successfully opened
[0x854d2a8] main xml debug: looking for xml module: 2 candidates
[0x854d2a8] main xml debug: using xml module "xtag"
[0x854d2a8] main xml debug: TIMER module_need() : 52.688 ms - Total 52.688 ms / 1 intvls (Avg 52.688 ms)
[0x854d138] playlist demux debug: parsed 0 tracks successfully
[0x854d2a8] main xml debug: removing module "xtag"
[0x85463b0] main input debug: EOF reached
[0x854d138] main demux debug: removing module "playlist"
[0x853db88] main stream debug: removing module "stream_filter_record"
[0x853e210] main access debug: removing module "access_file"
[0x85463b0] main input debug: TIMER input launching for 'Media Library' : 311.254 ms - Total 311.254 ms / 1 intvls (Avg 311.254 ms)
[0x8536838] main playlist debug: Activated
[0x8536838] main playlist debug: rebuilding array of current - root Playlist
[0x8536838] main playlist debug: rebuild done - 0 items, index -1
[0x8537490] main interface debug: looking for interface module: 1 candidate
[0x8537490] main interface debug: using interface module "hotkeys"
[0x8537490] main interface debug: TIMER module_need() : 54.389 ms - Total 54.389 ms / 1 intvls (Avg 54.389 ms)
[0x8537490] main interface debug: thread started
[0x8537490] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x854c140] main interface debug: looking for interface module: 1 candidate
[0x854c140] main interface debug: using interface module "inhibit"
[0x854c140] main interface debug: TIMER module_need() : 69.210 ms - Total 69.210 ms / 1 intvls (Avg 69.210 ms)
[0x854c140] main interface debug: thread started
[0x854c140] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x854a8e8] main interface debug: looking for interface module: 1 candidate
[0x854a8e8] main interface debug: using interface module "screensaver"
[0x854a8e8] main interface debug: TIMER module_need() : 82.726 ms - Total 82.726 ms / 1 intvls (Avg 82.726 ms)
[0x854a8e8] main interface debug: thread started
[0x854a8e8] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x84a5308] main interface debug: looking for interface module: 1 candidate
[0x84a5308] main interface debug: using interface module "signals"
[0x84a5308] main interface debug: TIMER module_need() : 5.318 ms - Total 5.318 ms / 1 intvls (Avg 5.318 ms)
[0x84a5308] main interface debug: thread started
[0x84a5308] main interface debug: thread ended
[0x84a5308] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x854eb78] main interface debug: looking for interface module: 0 candidates
[0x854eb78] main interface error: no interface module matched "globalhotkeys,none"
[0x854eb78] main interface debug: TIMER module_need() : 2.329 ms - Total 2.329 ms / 1 intvls (Avg 2.329 ms)
[0x854eb78] main interface error: no suitable interface module
[0x84a5140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x84a5140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x854ec58] main interface debug: looking for interface module: 4 candidates
[0x854ec58] main interface debug: using interface module "qt4"
[0x854ec58] main interface debug: TIMER module_need() : 7584.063 ms - Total 7584.063 ms / 1 intvls (Avg 7584.063 ms)
[0x854ec58] main interface debug: thread started
[0x854ec58] main interface debug: thread ended
[0x854ec58] main interface debug: thread (interface) created at priority 0 (interface/interface.c:151)
[0x854ec58] qt4 interface debug: Error while initializing qt-specific localization
[0x8536838] main playlist debug: adding item `dvd:///dev/sr0' ( dvd:///dev/sr0 )
[0x854ec58] qt4 interface debug: Adding a new MRL to recent ones: dvd:///dev/sr0
[0x8536838] main playlist debug: rebuilding array of current - root Playlist
[0x8536838] main playlist debug: rebuild done - 1 items, index -1
[0x8536838] main playlist debug: processing request item dvd:///dev/sr0 node null skip 0
[0x8536838] main playlist debug: resyncing on dvd:///dev/sr0
[0x8536838] main playlist debug: dvd:///dev/sr0 is at 0
[0x8536838] main playlist debug: starting new item
[0x8536838] main playlist debug: creating new input thread
[0xb6e006d8] main input debug: Creating an input for 'dvd:///dev/sr0'
[0xb6e006d8] main input debug: thread started
[0xb6e006d8] main input debug: using timeshift granularity of 50 MBytes
[0xb6e006d8] main input debug: using timeshift path '/tmp'
[0xb6e006d8] main input debug: thread (input) created at priority 10 (input/input.c:230)
[0x854ec58] qt4 interface debug: IM: Setting an input
[0xb6e006d8] main input debug: `dvd:///dev/sr0' gives access `dvd' demux `' path `/dev/sr0'
[0xb6e006d8] main input debug: creating demux: access='dvd' demux='' path='/dev/sr0'
[0x876e690] main demux debug: looking for access_demux module: 2 candidates
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
[0x876e690] dvdnav demux warning: cannot open dvdnav
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
[0x876e690] dvdread demux error: DVDRead cannot open source: /dev/sr0
[0x876e690] main demux warning: no access_demux module matching "dvd" could be loaded
[0x876e690] main demux debug: TIMER module_need() : 311.285 ms - Total 311.285 ms / 1 intvls (Avg 311.285 ms)
[0xb6e006d8] main input debug: creating access 'dvd' path='/dev/sr0'
[0x8770a38] main access debug: looking for access module: 0 candidates
[0x8770a38] main access error: no access module matched "dvd"
[0x8770a38] main access debug: TIMER module_need() : 1.899 ms - Total 1.899 ms / 1 intvls (Avg 1.899 ms)
[0xb6e006d8] main input error: open of `dvd:///dev/sr0' failed: no access module matched "dvd"
[0x854ec58] qt4 interface debug: Updating the geometry
[0xb6e006d8] main input debug: thread ended
[0x8536838] main playlist debug: dead input
[0x8536838] main playlist debug: changing item without a request (current 0/1)
[0x8536838] main playlist debug: nothing to play
[0x854ec58] qt4 interface debug: Updating the geometry
[0x854ec58] qt4 interface debug: IM: Deleting the input
[0x854ec58] qt4 interface debug: Updating the geometry
[0x854ec58] qt4 interface debug: Updating the geometry
[0xb6e006d8] main input debug: TIMER input launching for 'dvd:///dev/sr0' : 1772.111 ms - Total 1772.111 ms / 1 intvls (Avg 1772.111 ms)
[0x84a5140] main libvlc debug: deactivating the playlist
[0x8536838] main playlist debug: Deactivate
[0x8536838] main playlist debug: saving Media Library to file /home/lovinguniverse/.local/share/vlc/ml.xspf
[0x8536838] main playlist debug: looking for playlist export module: 1 candidate
[0x8536838] main playlist debug: using playlist export module "export"
[0x8536838] main playlist debug: TIMER module_need() : 39.984 ms - Total 39.984 ms / 1 intvls (Avg 39.984 ms)
[0x8536838] main playlist debug: removing module "export"
[0x8536838] main playlist debug: Deactivated
[0x84a5140] main libvlc debug: removing all services discovery tasks
[0x84a5140] main libvlc debug: removing all interfaces
[0x854ec58] qt4 interface debug: Quitting the Qt4 Interface
[0x854ec58] qt4 interface debug: destroying the main Qt4 interface
[0x854ec58] qt4 interface debug: Destroying the main interface
[0x854ec58] main interface debug: removing module "qt4"
[0x84a5308] main interface debug: removing module "signals"
[0x854a8e8] main interface debug: removing module "screensaver"
[0x854c140] main interface debug: removing module "inhibit"
[0x8537490] main interface debug: removing module "hotkeys"
[0x84a5140] main libvlc debug: removing playlist
[0x8536838] main playlist debug: Destroyed
[0x84a5140] main libvlc debug: TIMER ML Load : Total 369.045 ms / 1 intvls (Avg 369.045 ms)
[0x84a5140] main libvlc debug: TIMER Items array build : Total 1.887 ms / 2 intvls (Avg 0.944 ms)
[0x84a5140] main libvlc debug: TIMER ML Dump : Total 84.534 ms / 1 intvls (Avg 84.534 ms)
[0x84a5140] main libvlc debug: removing stats
[0x84a5140] main libvlc debug: removing module "memcpymmxext"
[0x84a5140] main libvlc debug: opening config file (/home/lovinguniverse/.config/vlc/vlcrc)
[0x84a5140] main libvlc debug: writing plugins cache /home/lovinguniverse/.cache/vlc/plugins-04041e.dat
libdvdnav: Using dvdnav version 4.1.3
libdvdnav: vm: failed to open/read the DVD
```

I seam to not get the 90 nubers? In terminal the earlier suggested packages will not install with the message "either outdated or not available".

---

### Post by mc4man on 2009-10-21
Well it's pretty straightfoward 
> libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
[0x876e690] dvdnav demux warning: cannot open dvdnav
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
[0x876e690] dvdread demux error: DVDRead cannot open source: /dev/sr0
[0x876e690] main demux warning: no access_demux module matching "dvd" could be loaded
......[0x8536838] main playlist debug: nothing to play

In other words it's not finding any filesystem to play.

This points to a dvd drive that's having trouble, ie either dirty or dying or both or disc's with physical damage
> Ubuntu has difficulties recognising media when I'm putting in the dvd. It cannot mount DVDs very well, and I have to open the DVD rom and close it again a couple of time before any icon appears on the desktop, or leave it in for a very long time.

DVD rom is very active when DVD is installed, I hear sounds an some kind of action but no recognition of media. 



With a dvd in the drive and the drive settled run this
```
sudo lahw -C disk
```

You should see something similar under the cdrom entry, note blue
>  *-cdrom:0               
       description: DVD-RAM writer
       product: DVD A  DH20A4P
       vendor: ATAPI
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 9P59
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.[COLOR="Blue"]fstype=udf[/COLOR] mount.options=ro,nosuid,nodev,relatime,utf8 [COLOR="Blue"]state=mounted status=ready[/COLOR]
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.[COLOR="Blue"]fstype=udf[/COLOR] mount.options=ro,nosuid,nodev,relatime,utf8 [COLOR="Blue"]state=mounted[/COLOR]

---

### Post by 2blue on 2009-10-21
In terminal I get "command not found" ? 

and when trying open DVD from VLC I get

Playback failure:
DVDRead could not open the disc "/dev/sr0".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.
Playback failure:
DVDRead could not open the disc "/dev/sr0".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details

---

### Post by mc4man on 2009-10-21
Sorry, it's late here, mistyped command

```
sudo lshw -C disk
```

---

### Post by 2blue on 2009-10-21
I get this in terminal: 

lovinguniverse@lovinguniverse-laptop:~$ sudo lshw -C disk
[sudo] password for lovinguniverse: 
  *-disk                  
       description: ATA Disk
       product: SAMSUNG HM100JC
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: YN10
       serial: S0CFJ10A147384
       size: 93GiB (100GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=502e4d3b
  *-cdrom
       description: DVD writer
       product: DVD-RW GWA-4082N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: CW02
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted
lovinguniverse@lovinguniverse-laptop:~$

---

### Post by mc4man on 2009-10-21
Your lshw looks fine, though it still is likely your drive and or disc condition is a bit of an issue.
Try this without a dvd in the drive
First go into home folder and delete the .dvdcss folder (hidden folder, if you don't see it go Ctrl+h on keyboard

Then in terminal go
```
nautilus-file-management-properties
```

Under the media tab for dvd video set vlc as the default player

Then put your dvd in and see what happens, vlc shouldn't open till the disk is detected and mounted.

( have you tried any other players like mplayer

---

### Post by 00ber n00b on 2009-10-21
I am having the same issue.  I've got the movie to play back once by de-installing/re-installing, but, now the drive doesn't even recognize the media.  It doesn't even show up on the desktop, this is with multiple movies.  Also using Karmic.

---

### Post by 00ber n00b on 2009-10-21
*-disk                  
       description: ATA Disk
       product: WDC WD2500BEVS-2
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WXE308FA2221
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=7908213a
  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GSA-T20F
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: EG02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb

---

### Post by bhspencer on 2009-10-21
Yep 

exactly the same problem here. The drive is brand new and I just used it to install 9.10 so I am inclined to belive this is a software problem.

 *-cdrom
       description: DVD-RAM writer
       product: DVD RW AD-7560S
       vendor: Optiarc
       physical id: 1
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: SX01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

---

### Post by 00ber n00b on 2009-10-21
> **bhspencer said:**
> Yep 

exactly the same problem here. The drive is brand new and I just used it to install 9.10 so I am inclined to belive this is a software problem.

 *-cdrom
       description: DVD-RAM writer
       product: DVD RW AD-7560S
       vendor: Optiarc
       physical id: 1
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: SX01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

Neither mine or your's says anything about being mounted?!?

---

### Post by rustutzman on 2009-10-21
I was having similar problems and ended up installing Kaffeine from the repositories. It installed the required kde dependencies and has worked out pretty good. HTH

Russ

---

### Post by 00ber n00b on 2009-10-21
Don't know if it'll help but I have 64 bit everything...AMD64, ubuntu 9.10 64, firefox 64 bit, adobe flash 64 bit(alpha stage)

---

### Post by 00ber n00b on 2009-10-21
> **rustutzman said:**
> I was having similar problems and ended up installing Kaffeine from the repositories. It installed the required kde dependencies and has worked out pretty good. HTH

Russ

I'll try that right now.

---

### Post by 00ber n00b on 2009-10-21
> **00ber n00b said:**
> I'll try that right now.

 At first when the drive was inactive and the movie didn't show up on my desktop I got...Cannot find plugin for MRL (DVD:/).  Now, I FINALLY got the movie to load once and I get...Cannot find demultiplexer plugin for MRL (DVD:/).  This is with kaffeine.  

With Mplayer I get...No URI handler for "DVD".

Gonna install VLC again and see what happens.

---

### Post by 00ber n00b on 2009-10-21
VLC is playing now.  I don't know why it's so unstable.

---

### Post by 00ber n00b on 2009-10-21
It's still sluggish trying to find the media in the drive.

---

### Post by cariboo on 2009-10-21
Are you getting ny error messages in dmesg when the dvd is trying to mount?

To check open a terminal and type:

```
dmesg | tail -n20
```

---

### Post by 00ber n00b on 2009-10-21
> **cariboo907 said:**
> Are you getting ny error messages in dmesg when the dvd is trying to mount?

To check open a terminal and type:

```
dmesg | tail -n20
```

dmesg | tail -n20
[ 5285.278542] sr 4:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[ 5285.278542] end_request: I/O error, dev sr0, sector 16023104
[ 5285.278542] Buffer I/O error on device sr0, logical block 4005776
[ 5285.278542] Buffer I/O error on device sr0, logical block 4005777
[ 5285.893696] UDF-fs: Partition marked readonly; forcing readonly mount
[ 5285.966822] UDF-fs INFO UDF: Mounting volume 'SIDEWAYS_43', timestamp 2005/02/11 01:19 (1f10)
[ 6309.831257] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6309.831263] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 6309.831268] sr 4:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[ 6309.831277] end_request: I/O error, dev sr0, sector 16023104
[ 6309.831282] Buffer I/O error on device sr0, logical block 4005776
[ 6309.831286] Buffer I/O error on device sr0, logical block 4005777
[ 6309.836120] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6309.836125] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[ 6309.836130] sr 4:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[ 6309.836137] end_request: I/O error, dev sr0, sector 16023104
[ 6309.836142] Buffer I/O error on device sr0, logical block 4005776
[ 6309.836145] Buffer I/O error on device sr0, logical block 4005777
[ 6309.971289] UDF-fs: Partition marked readonly; forcing readonly mount
[ 6310.135851] UDF-fs INFO UDF: Mounting volume 'SIDEWAYS_43', timestamp 2005/02/11 01:19 (1f10)

This is of course with the dvd already mounted and just sitting in the drive not playing.

---

### Post by 2blue on 2009-10-21
If I let Karmic Koala develop naturally and install all updates will this driver / plugin problem fix it's self?

---

### Post by 2blue on 2009-10-22
I have spent hours trying to find a solution for my DVD player, and it looks like it's not going to be fixed any time soon. I booted Puppy Linux as live CD to see if DVDs would play and it works all right. Puppy comes with Xine media player, that is why I installed it from Synatic, but on Karmic Koala it doesn't work. Is this normal? 

What do you Ubuntu experts think: Is it likely a bug or most likely a configuration problem?

---

### Post by 2blue on 2009-10-22
After yet another go at it, I discovered there is probably a difference between gxine and plane Xine. Sorry I am a bit slow at this. After some work Xine will play DVD both region 1 and 2, which this laptop never did before. However, it still protests with error messages "cannot read file", "cannot mount volume", and there is also a report of missing drivers or plugins not properly working :confused:

I have decided to live with this at least as long as the Karmic beta version lasts. 

Any thoughts on the subject is still very much appreciated  :P

---

