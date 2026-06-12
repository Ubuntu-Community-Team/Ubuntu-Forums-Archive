---
title: "gnome-session under Xvnc broken following upgrade"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Roland of Gilead on 2007-04-20
So, I upgraded to 7.04, basically without incident.  The system in question is a Dell Dimension XPS_T800 (800MHz Piii), acting as a fileserver.  It has only a keyboard...no mouse, no monitor.  I control the box entirely by SSH or VNC

My Xvnc4 config is not integrated with the gdm...that is to say, it's a separate process running fulltime.  In fact, my default machine configuration doesn't even load the gdm (redhat type distros call this runlevel 3).

So anyhow...after I upgrade and reboot, things seem to be fine.  Then I edit my /etc/apt/source.list to re-enable my universal updates.  After this, the update manager finds new versions of the Xvnc4 packages, which I allow it to update.

I recycle the vncserver process, and reconnect...only to find just a blank grey screen.  No gnome desktop. 

So, I look in the Xvnc log file and find this (below).  I ignore the ipv6 stuff, as I have ipv6 blacklisted in my modprobe config.

```
root@scorpio:/etc/init.d# cat /home/christopher/.vnc/scorpio\:1.log
_XSERVTransSocketOpenCOTSServer: Unable to open socket for inet6
_XSERVTransOpen: transport open failed for inet6/scorpio:2
_XSERVTransMakeAllCOTSServerListeners: failed to open listener for inet6

Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Fri Apr 20 13:48:46 2007
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
access control disabled, clients can connect from any host
The program 'gnome-session' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 74 error_code 1 request_code 146 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by buddijeevi on 2007-04-22
Hi
   ii  xvnc4viewer                            4.1.1+xorg1.0.2-0ubuntu4             
  Virtual network computing client software fo

ii  xserver-xorg-core                      1.2.0-3ubuntu8                         X.Org X server -- core server

It looks like xvnc is compiled against old version of xorg. If you compile xvnc with xorg1.2.0, it will work.

---

### Post by geek.de.nz on 2007-08-12
This issue was still there for me. After a bit of googling and looking i found out that making your /etc/xinetd.d/Xvnc file look like this helps:

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

---

