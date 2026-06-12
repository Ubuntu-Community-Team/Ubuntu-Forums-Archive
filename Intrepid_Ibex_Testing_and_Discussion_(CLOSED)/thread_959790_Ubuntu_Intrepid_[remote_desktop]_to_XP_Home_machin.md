---
title: "Ubuntu Intrepid [remote desktop] to XP Home machine miiiiiles away?"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Roasted on 2008-10-26
A relative of the family is having some issues with his email, yet I'm sure it's something simple.

I've worked with remote desktop on LANs, but is there anyway I can do that from my Ubuntu machine over to his?

I'm running Intrepid Beta 64 bit currently.

---

### Post by tuskenraider on 2008-10-26
well to RDP his machine would have to be xp pro media center edition or a vista version thats business or ultimate.  i would sugguest tight vnc.  Have him download and install tightvnc forward the appropriate port to the computer to be accessed and connect to his computer via your favorite vnc program.  I personally use gnome-rdp.


enjoy

wait... is his box an ubuntu box??  then set up vnc in ubuntu on his and vnc to his via your fav connection program.

---

### Post by ciscosurfer on 2008-10-26
You could also use vinagre, a remote desktop viewer (it's in the latest 8.10 RC).  

I'm slightly biased towards vnc, though,  b/c I use it all time, so that would be my ultimate suggestion as well.

---

### Post by tuskenraider on 2008-10-26
> **ciscosurfer said:**
> You could also use vinagre, a remote desktop viewer (it's in the latest 8.10 RC).  

I'm slightly biased towards vnc, though,  b/c I use it all time, so that would be my ultimate suggestion as well.

thats a nice looking little program there... thanks for letting us know about it... i might switch from gnome-rdp over to vinagre to see how i like it... preciate that.

tusken

---

### Post by ciscosurfer on 2008-10-26
> **tuskenraider said:**
> thats a nice looking little program there... thanks for letting us know about it... i might switch from gnome-rdp over to vinagre to see how i like it... preciate that.

tuskensure thing :)

---

### Post by ryanhaigh on 2008-10-26
If you are the tech support guy for friends/family I recommend using VNC because it is available on all platforms.

I don't know if Vinagre has this capability (it is also a VNC client) but using one of the command line applications (xvnc4viewer or xtightvncviewer) you can run a listening client (refer to the man pages for further details) on your computer and forward the appropriate port so that those your helping don't need to worry about messing with firewall/router configurations, they simply use a reverse connection in tightvnc I believe the option is 'Add a client'.

The other thing you will need to know is your external ip address but there are plenty of sites where you can find that or you can use dyndns or similar to provide a recognisable address for them to use.

Setting up your system with port forwarding and the listening vnc client is a lot easier and faster than trying to explain port forwarding and router configuration (particularly if you aren't familiar with their router) every time you need to help someone. This way all they do is install the software, click add client and enter your ip/dns name:port that the client is listening on)

---

### Post by d_skillz on 2008-10-26
this really helps

---

### Post by forger on 2008-10-26
> **tuskenraider said:**
> thats a nice looking little program there... thanks for letting us know about it... i might switch from gnome-rdp over to vinagre to see how i like it... preciate that.

tusken

vinagre is installed by default with gnome since ubuntu 8.04 hardy! Applications > Internet > Remote Desktop Viewer :)

---

### Post by bodhi.zazen on 2008-10-26
Another option is FreeNX, also available on multiple OS (Linux + Windows). Bit faster and more secure, IMO.

The other issue is if your parents have a router. If so they will need to forward the relevant ports and you need to know their public IP address.

Exact details on how to do this vary with routers.

---

