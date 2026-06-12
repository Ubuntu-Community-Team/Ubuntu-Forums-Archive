---
title: "VNC Startup Issue"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by Merrigan on 2007-06-03
Hi There,

I have moved to Kubuntu Feisty Fawn about a week ago, and I must say that I am extremely impressed. I have installed vnc server on the system, as I want to be able to access the machine from my office as well.

My problem, however is that VNC doesn't want to start. It shoves out this nasty error, and I am unable to find an answer for it. I have never had any issue of this sorts with vnc server, so I am totally dumbstruck.

Any Help would be appreciated!!

The Error:

```
xauth: (argv):1:  bad display name "aragorn.lewendewoord.co.za:1" in "add" command
```

 -- Merrigan

---

### Post by buntunub on 2007-12-17
same problem here

---

### Post by buntunub on 2007-12-18
Any ideas on this issue? Ive tried moving the .Xauth file so that it creates a new one; no joy. This only just started happening since the latest updates, and until then, I was able to vnc in with no issues for the last several months. Google turns up almost nothing about this.

---

### Post by buntunub on 2007-12-18
It occurred to me that when initially setting up vncserver, that you must first set it up with

[PHP] $vncserver[/PHP]

which will then go on to setup your vnc server with passwords and a local xauth file. I had done this, and have been using it for some time now without issue until last Friday when this error reared its ugly head. On a whim, ill give this a shot and see if it fixes things. If so, it indicates that somehow, the server reset itself after the latest round of upstream updates. Im on an x86_64 machine so that could have a very remote chance of mucking with things too, albiet ~very~ remote. Anyway, if anyone has any ideas on this issue, please chime in. Oh by the way, the error logs on /home/xxxx/.vnc/xxxx:1.log indicate that the .Xauth cant be found, or something like that.

---

### Post by buntunub on 2007-12-18
This did not work, although some things did happen:

[PHP]$vncserver
xauth:  creating new authority file /home/davemc/.Xauthority
xauth: (argv):1:  bad display name "davemc:1" in "add" command
xauth:  creating new authority file /home/davemc/.Xauthority

New 'X' desktop is davemc:1

Starting applications specified in /home/davemc/.vnc/xstartup
Log file is /home/davemc/.vnc/davemc:1.log[/PHP]

here is the logfile:

[PHP]18/12/07 17:27:13 Xvnc version 3.3.tight1.2.9
18/12/07 17:27:13 Copyright (C) 1999 AT&T Laboratories Cambridge.
18/12/07 17:27:13 Copyright (C) 2000-2002 Constantin Kaplinsky.
18/12/07 17:27:13 All Rights Reserved.
18/12/07 17:27:13 See http://www.uk.research.att.com/vnc for information on VNC
18/12/07 17:27:13 See http://www.tightvnc.com for TightVNC-specific information
18/12/07 17:27:13 Desktop name 'X' (davemc:1)
18/12/07 17:27:13 Protocol version supported 3.3
18/12/07 17:27:13 Listening for VNC connections on TCP port 5901
Font directory '/usr/share/fonts/X11/cyrillic' not found - ignoring
Font directory '/usr/share/fonts/X11/CID' not found - ignoring
Font directory '/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID' not found - ignori$
xrdb: No such file or directory
xrdb: can't open file '/home/davemc/.Xresources'
Option --login is no longer supported in this version of gnome-terminal; you mi$
Window manager warning: Log level 32: could not find XKB extension.[/PHP]


when i try to connect via client, I get this:

[PHP] vncviewer -via davemc@xxx.xxx.xxx.xxx davemc:1

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 17:17:04
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Tue Dec 18 17:43:22 2007
 CConn:       connected to host localhost port 5599
channel 3: open failed: administratively prohibited: open failed
 main:        End of stream[/PHP]


Any ideas?

---

### Post by buntunub on 2007-12-18
This problem really has me buggered. None of the usual tricks worked to solve this thing. On a whim, and after MUCH futzing around, I decided to try the 'ol 

$vncviewer -via blah blah localhost:1

And that worked! Weirdest thing ever. The original issue still persists in that it refuses to recognize the server names and seems to default to localhost now. This is entirely new, as I have been using the hostname for over a year now to login with no issues whatever. Well, whatever. Its working now (kind of), but the issue persists. I just wonder if, because its an xrdb and xauth issue, if this is going to bleed over into far more serious issues with Xservers and logins.

---

