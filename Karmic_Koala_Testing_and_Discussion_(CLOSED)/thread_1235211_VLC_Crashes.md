---
title: "VLC Crashes"
date: 2009-08-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by AlanR8 on 2009-08-08
Sony Vaio laptop as in my sig line

On a clean install of Ubuntu all is fine and VLC plays. 

If I enable effects and install Cairo Dock, which I have, VLC just opens and closes.

Have reported the issue but has anyone any ideas?

---

### Post by wayne_cat on 2009-08-08
> **AlanR8 said:**
> Sony Vaio laptop as in my sig line

On a clean install of Ubuntu all is fine and VLC plays. 

If I enable effects and install Cairo Dock, which I have, VLC just opens and closes.

Have reported the issue but has anyone any ideas?


try to start vlc from gnome-terminal ... you should see an error message

---

### Post by AlanR8 on 2009-08-09
A little bit more info for you all.

Never a problem with VLC under Kubuntu, and as I said in my first post on a clean install on Ubuntu Karmic it works. I could open and play .avi files etc.

Having done all the updates including dist-upgrades, I can no longer use Alt+F2 to bring up a command line, and whilst VLC will open the minute I ask it to play a movie file it just closes. Oddly, it will play music files.

Movie Player will play the video files. I installed the medibuntu repos and installed w32codecs libdvdcss2, and in the past that's all I've had to do to play anything including DVDs. I also found out last night that Movie Player will play DVDs but there's no sound!

To cap it all, VLC plays perfectly on my EeePC running Karmic Netbook Remix that's also fully up to date.

---

### Post by jmmL on 2009-08-09
You need to start VLC from a terminal like the previous poster suggested. VLC should hopefully then throw an error message.

Try 
```
vlc -v
``` to get verbose output.

---

### Post by AlanR8 on 2009-08-09
Will give it a go

---

### Post by taavikko on 2009-08-09
Think this is worth mentioning,
been awhile since I used vlc but noticed weird behaviour when fumbling with the settings.
Looked like when one sets the video-output module to something that videocard doesn't support, it results a segfault.

So try resetting to defaults
```
rm -r ~/.config/vlc/
```
and restarting.

---

### Post by AlanR8 on 2009-08-16
Solved with a clean install of Alpha 4

---

### Post by soapytheclown on 2009-08-16
> **AlanR8 said:**
> Solved with a clean install of Alpha 4

i had the same problem as you described it seemed to occur after installing cario dock too, i uninstalled cario dock, remvoed the old config files and vlc -v produces the following error:

[PHP]
vlc -v
VLC media player 1.0.1 Goldeneye
[0x2203458] main demux warning: no access_demux module matching "file" could be loaded
[0x2201338] main interface error: no interface module matched "globalhotkeys,none"
[0x2201338] main interface error: no suitable interface module
[0x210a888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x210a888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x28de928] mp4 stream warning: unknown box type alis (incompletely loaded)
[0x28de928] mp4 stream warning: Not enough data
[0x28de928] mp4 stream warning: unknown box type      (incompletely loaded)
[0x28de928] mp4 stream warning: unknown box type tapt (incompletely loaded)
[0x28de928] mp4 stream warning: unknown box type alis (incompletely loaded)
[0x28de928] mp4 stream warning: unknown box type colr (incompletely loaded)
[0x28de928] mp4 stream warning: unknown box type      (incompletely loaded)
[0x239d4c8] mp4 demux warning: elst box found
[0x239d4c8] mp4 demux warning: elst box found
[0x239d4c8] mp4 demux warning: control query 14 unimplemented
[0x239d4c8] mp4 demux warning: DEMUX_GET_FPS unimplemented !!
[0x7f534005aa08] faad decoder warning: decoded zero sample
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x4004718] freetype spu text warning: unbreakable string
[0x3e71348] main audio output warning: PTS is out of range (-17725), dropping buffer
[????????] x11 video output error: X11 request 133.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  133 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  101
  Current serial number in output stream:  102
[/PHP]

on a side note im using the nvidia drivers and im still getting weird colours being used for videos when telling gstreamer-properties to autodetect or set to X11/Xshm/xv if i use no xv then colours are normal but obv im not using hardware acceleration

---

### Post by nhasian on 2009-08-20
can someone confirm this bug and add any other info they feel is relevant.  thanks!

[https://bugs.launchpad.net/cairo-dock-core/+bug/416294](https://bugs.launchpad.net/cairo-dock-core/+bug/416294)

---

### Post by fabounet on 2009-08-22
the bug has been transferred to Qt (it's a Qt issue)
waiting for their answer...
until then, in VLC, uncheck the option "integrate video into interface"

---

### Post by nstorrs on 2009-09-12
I'm having the same problem ('no access_demux module matching "file" could be loaded' and 'X Error: BadWindow' etc) after installing pulse audio volume changer. I was wondering if anyone has manage to find a fix.

---

