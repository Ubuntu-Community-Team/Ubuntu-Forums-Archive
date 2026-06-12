---
title: "xine won't load from command line Ubuntu Intrepid Ibex"
date: 2008-09-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Robertjm on 2008-09-06
Hi all,

After my recent reinstall I discovered I had wobby windows!! Yes, Beryl/compiz decided to start working all on its own for whatever reason. Unfortunately, I've also discovered that I can no longer pay DVDs in my drive.

xine-gui kept shutting down as fast as it started so I finally loaded xine at the command line to see what kind of errors I might be getting. Here's what I got:

[b][color=blue]robertjm@desktop:~$ xine
This is xine (X11 gui) - a free video player v0.99.6cvs.
(c) 2000-2007 The xine Team.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  2463
  Current serial number in output stream:  2464
robertjm@desktop:~$ 
[/color][/b]

After doing some pawing around on th Internet I was able to get VLC working...kind of. I'm getting choppy video, which is something I had under Hardy before upgrading to Intrepid. Another side issue is that after a few seconds the colors go grey, as if the VLC player wasn't the active window. As soon as I clicked on the video it came back, only to go grey again.

Any idea how to fix xine? That's my program of choice. I've even tried reinstalling. However, that didn't seem to cure anything.

Robert

---

### Post by wolfen69 on 2008-09-06
my guess is that your video drivers are conflicting. have you uninstalled them to see if the problem goes away?

---

### Post by Robertjm on 2008-09-06
OK. So I installed and ran EnvyNG to install the proprietary ATI driver. (I'm using an X1600 AGP video card). 

After rebooting it refuses to detect my video card. I allow it to use the defaults, which is something like 800x600, or thereabouts. Compiz/XGL no longer loads. However, my video seems to play just fine in gxine. Since t wouldn't allow me to change the screen resolution I went ahead and deactivated the ATI driver in the restricted drivers window. What that really did was uninstall the restricted driver. AFter I restarted, back came the wobbly windows and back came compiz/XGL, and back came the DVD problems!

If its DVDs vs. wobby windows, I'll take the DVD thank you very much. I just need to be able to edit the resolution though to accept my Samsung 22" widescreen monitor!

Robert

---

### Post by Robertjm on 2008-09-06
I got a workaround for now. When starting my computer I choose the Failsafe Gnome option, which doesn't do all the scripting loading. This effectively shuts down compiz and allows me to run the movie just fine.

Robert

---

