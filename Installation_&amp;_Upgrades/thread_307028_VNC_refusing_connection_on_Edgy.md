---
title: "VNC refusing connection on Edgy"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by rleck on 2006-11-26
My remote, headless music box refuses vnc connections after the edgy upgrade. This happened after the Dapper upgrade, but re-enabling the Remote Desktop did the trick in 1 minute. Not so this time. Ironically, if I put a keyboard and monitor on it, then reset the password for the Remote Desktop, everything will work as normal, until I reboot. Then I go back to a failed authentication message. This is a straight over the LAN Edgy to Edgy connection. Any ideas? :neutral:

---

### Post by froped on 2006-11-26
I have experienced the same thing. It also seems impossible to connect to the machine if no user is logged in. Is this a vino spesific configuration? Maybe I should try a different VNC-server.

---

### Post by PurpleSun on 2006-11-26
I had the same problem but it seems fixed now with the new Vino update.

The new Vino 2.16.0-unbuntu2.1 in proposed update repository fixes the problem. Go into Synaptic and activate proposed updates repository. Search for Vino in Synaptic and manually update from 2.16.0-ubuntu2 to 2.16.0-ubuntu2.1.

Been working fine for me for the past day. I have restarted my headless PC over 20 times with no sign of the password problem.

---

### Post by bluecat9 on 2006-11-27
sudo vi /etc/inetd.conf

..

#vnc server (Dapper)
5900    stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -inetd -IdleTimeout 7200 -depth 16 -SecurityTypes None -Desktop "My Ubuntu Box" -once -query localhost

#vnc server (Edgy)
5900 stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -fp /usr/share/fonts/X11/misc/ -inetd -IdleTimeout 7200 -depth 16 -SecurityTypes None -Desktop "My Ubuntu Box" -once -query localhost

..

Write changes and restart inetd.

The key here for Edgy is the "-fp <fonts_dir>" at the beginning of the line.

Enjoy.

---

### Post by rleck on 2006-11-28
I should have been patient! I flipped my music box back to Dapper as all atempts to get a VNC version to work had failed. Thanks for the feedback and the solutions!

---

### Post by mckemie on 2006-11-30
> **bluecat9 said:**
> sudo vi /etc/inetd.conf

..

#vnc server (Dapper)
5900    stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -inetd -IdleTimeout 7200 -depth 16 -SecurityTypes None -Desktop "My Ubuntu Box" -once -query localhost

#vnc server (Edgy)
5900 stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -fp /usr/share/fonts/X11/misc/ -inetd -IdleTimeout 7200 -depth 16 -SecurityTypes None -Desktop "My Ubuntu Box" -once -query localhost

..

Write changes and restart inetd.

The key here for Edgy is the "-fp <fonts_dir>" at the beginning of the line.

Enjoy.

Are those two lines in the /etc/initd.conf file?  Or, are line breaks not signigicant?

How does one restart initd?  I have no /etc/init.d/initd.  The command "initd" doesn't do it.

[https://help.ubuntu.com/community/VNC?highlight=%28vnc%29](https://help.ubuntu.com/community/VNC?highlight=%28vnc%29)
talks about /etc/init.d/xinitd, also missing from my install.

I, too, am working on a headless music server.

---

### Post by froped on 2006-12-03
I tried this last suggested solution and i also tried "vncserver" without success. I got respons from the server both times but the desktop was not displayed, just a blank screen. I tried x11vnc and it works. If no user is logged into an X session you will get the X greeter login.

---

### Post by mckemie on 2006-12-03
> **froped said:**
> I tried this last suggested solution and i also tried "vncserver" without success. I got respons from the server both times but the desktop was not displayed, just a blank screen. I tried x11vnc and it works. If no user is logged into an X session you will get the X greeter login.

Thanks for the suggestion!

On the server side, I tried:
root@sff-dapper-b:~# x11vnc -display :0 -auth /var/gdm/:0.Xauth
and got:
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Care to share the two x11vnc commands you are using?

For those who know even less than I about this X remote control stuff, I offer several options:
1) ssh -XC <hostIP>
    after login, start X apps such as xmms, gnome-terminal, etc which will display remotely.  In the host's /etc/ssh/sshd_config, "X11Forwarding yes".  Then, restart ssh: /etc/init.d/ssh restart
2) X -query <hostIP> :1
     this will get you the whole X kit and kiboddle on another (probably F8) virtual console.  XDMCP must be enabled in "server's" /etc/gdm/gdm.conf.  Restart gdm: /etc/init.d/gdm restart
3) the multiple VNC options being explored here.

---

### Post by zakhooi on 2006-12-09
Now there is another update for vino-server (2.16.0-0ubuntu2.2) and this time it made things worse.
It only accepts clients that support protocol version 3.7 (see also [http://www.ubuntuforums.org/showthread.php?t=314786](http://www.ubuntuforums.org/showthread.php?t=314786) )
But eventhough I use a client that supports version 3.7 (xvnc4viewer) it still wont accept the connection:

```
$ xvnc4viewer linux:0

VNC Viewer Enterprise Edition E4.2.7 for X - built Oct 16 2006 13:50:32
Copyright (C) 2002-2006 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.


Sat Dec  9 10:58:14 2006
 TcpSocket:   connected to 192.168.175.101::5900
 CConn:       Connected to host linux port 5900
 CConn:       Encryption set to 'Server'
 CConnection: Server supports RFB protocol version 3.7
 CConnection: Using RFB protocol version 3.7
 CConn:       Closed: End of stream
```

Any ideas?

---

### Post by toaday on 2006-12-10
[http://blogs.vislab.usyd.edu.au/index.php/VNCProxy/2006/11/28/getting_vncserver_to_run_on_ubuntu_edgy_10](http://blogs.vislab.usyd.edu.au/index.php/VNCProxy/2006/11/28/getting_vncserver_to_run_on_ubuntu_edgy_10)

I just found that and it looks like that might be our solution, I've been having this problem for a while now too.

---

### Post by zakhooi on 2006-12-10
That's a different issue and does not solve the 'protocol 3.7' problem as mentioned above

---

### Post by toaday on 2006-12-10
Yep, it does the trick! Just have to restart your VNC server after those commands, assuming it was running.

---

### Post by mckemie on 2006-12-21
> **toaday said:**
> [http://blogs.vislab.usyd.edu.au/index.php/VNCProxy/2006/11/28/getting_vncserver_to_run_on_ubuntu_edgy_10](http://blogs.vislab.usyd.edu.au/index.php/VNCProxy/2006/11/28/getting_vncserver_to_run_on_ubuntu_edgy_10)

I just found that and it looks like that might be our solution, I've been having this problem for a while now too.

From the above link:
---
It seems that there is some problems with the default vncserver configuration for Ubuntu Edgy. VNCServer will complain that it can't find 'fixed' fonts.

This will fix it:
$bash> cd /usr/share/X11
$bash> sudo ln -s /usr/share/fonts/X11 fonts
---

However, it didn't fix mine.

---

### Post by shanepardue on 2006-12-26
Neither has it fixed mine. I have the same problem.

```
read: Connection reset by peer (104)
```

---

