---
title: "TightVNC server config"
date: 2005-05-22
forum: Installation &amp; Upgrades
---

### Post by popie on 2005-05-22
I installed tightvncserver, but when I connect to this ubuntu machine I see only a grey screen with a term window. How can I set this up to see a complete ubuntu gnome desktop?

My ~/.vnc/xstartup is as follows:

#!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &

---

### Post by popie on 2005-05-22
OK, I've made some progress by modifying the xstartup file to contain:

  exec gnome-session &

Now I see gnome, but it's still kind of broken. Basically all the admin stuff won't run and often gives the error 

  "Unable to copy the users Xauthorization file."

A few apps that won't run and display the above error:
Update manager
Package manager (Synaptic)
Users and groups
Time and date

Also, some icons are broken (trashcan, showdesktop)

Using vnc was SO easy with the other Linux distro I was using...(Mandrake) Was it because vnc w/ KDE works better that with Gnome? I can't believe just getting vnc running is taking so much effort! :) Of course I'm not a guru, that could have something to do with it. Basically I just want to run this box headless. If there's a better way I'm all ears.

---

### Post by imightbegiant on 2005-06-16
If you want to get to the default display (display:0) which is the one when you log in locally, it's easiest to go to system>preferences>remote desktop and enable the vnc server from there. If you want to have the gnome session for the spawned instances :1 :2 :3 ...etc that's another story...

---

### Post by popie on 2005-06-16
[QUOTE=imightbegiant]If you want to get to the default display (display:0) which is the one when you log in locally, it's easiest to go to system>preferences>remote desktop and enable the vnc server from there. If you want to have the gnome session for the spawned instances :1 :2 :3 ...etc that's another story...[/QUOTE]

Thanks. The real problem with that the built in remote desktop is that its incredibly SLOW. It is just so lethargic in responding that I wanted to instead use tightvnc or realvnc, both of which would be much snappier. I've done this on other distros, and it was very easy. Not on Umbutu.

Since I couldn't get vnc working adequately, and I'm no Linux guru, I sadly had to switch distros. On Mepis I simply installed vncserver and I was off and running. And the remote response is very fast.

---

### Post by imightbegiant on 2005-06-16
I don't really notice a performance difference in either vnc server, and I have full functionality with tightvnc running gnome.  If Mepis is working great, then more power to you. That's one of the pluses of linux, you're not happy with a distro, there's 1000 more to choose from.

Cheers

---

### Post by guilty on 2005-06-20
Hi all! 

I've installed tightvncserver on my computer and works fine, also with the java add-on.

I'd like to know if its possible to control the session :0 using it instead of use the vnc server integrated with the system because this one cannot be controlled with java.

---

### Post by digitalvoid on 2005-07-08
vino (the gnome vnc server used to "share" your desktop remotely) puts quite a load on my poor ol' (P3 733MHz) ubuntu box as compared to a regular Xrealvnc session.

Guilty: to share :0 you can use x11vnc.  It's not as peppy as Xrealvnc for :1 but it's much better than vino.  

I'm trying to setup tightvnc myself right now but for some reason it won't run my ~/.vnc/xstartup file (but realvnc will).  I just don't get why but I'll figure something out.

---

### Post by digitalvoid on 2005-07-08
[QUOTE=digitalvoid]I'm trying to setup tightvnc myself right now but for some reason it won't run my ~/.vnc/xstartup file (but realvnc will).  I just don't get why but I'll figure something out.[/QUOTE]
 LOL.... yeah, turns out those log things work well.

tightvnc actually executes the xstartup file which didn't have execute permission.  I wonder why realvnc handles it differently.  Well I don't wonder much... now that it's working.  ;)

---

### Post by djbon2112 on 2008-07-06
> **popie said:**
> I installed tightvncserver, but when I connect to this ubuntu machine I see only a grey screen with a term window. How can I set this up to see a complete ubuntu gnome desktop?

My ~/.vnc/xstartup is as follows:

#!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &

I've got a simmilar issue, BUT I'm running Ubuntu Server x64 (no GUI) on the server. Is there any way for TightVNC to start a GNOME desktop for VNC specifically, since I find that trying to install GNOME on the server installs is a PITA?

---

