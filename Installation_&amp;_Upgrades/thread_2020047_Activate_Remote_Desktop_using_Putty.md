---
title: "Activate Remote Desktop using Putty"
date: 2012-07-07
forum: Installation &amp; Upgrades
---

### Post by T18315C on 2012-07-07
Sorry for my english:)

First of all I would like to point out that I am very new to Linux. A few days ago I purchased a VPS, one of the available systems were Ubuntu, I chose it because it supposedly is well suited for beginners.
For now, just did the updates and installed the Ubuntu desktop. Now I want to activate remote desktop sharing, so as to connect to later using VNC. I searched a lot and I found just the way through the graphical environment. Is there a command to make it through putty?

---

### Post by T18315C on 2012-07-08
Thanks, I installed Teamviewer, unfortunately I do not know how to check ID and password using putty. All the tutorials show you how to do this using the graphical environment.:confused:

---

### Post by steeldriver on 2012-07-08
It's going to depend on exactly what desktop / session manager / xserver components (if any) you have already installed on the VPS and also whether you are going to be tunneling the VNC over SSH

Basically once the remote xserver (Xvnc / tightvncserver or whatever) is installed and setup, you would usually run it with a wrapper script called 'vncserver', either requesting a specific display number / port (useful if you are SSH tunneling, because your putty script can set up the tunnel ahead of time) or allowing it to choose the next available display and corresponding port number (by default, 5900 + display number)

If you google 'ubuntu vps vncserver' you should be able to find a bunch of walkthroughs - I've never done it with a VPS but this one looks pretty good to me:

[http://blog.cheapvps.co.uk/index.php/2011/03/29/how-to-setup-vnc-over-ssh-on-ubuntu-server/](http://blog.cheapvps.co.uk/index.php/2011/03/29/how-to-setup-vnc-over-ssh-on-ubuntu-server/)

If you are connecting *only* from Windows boxes, then you could consider using xrdp so that you can use the native Remote Desktop client instead of requiring a 3rd party VNC client on the Windows side (although I've seen mixed reports about xrdp - especially on 12.04 - VNC is probably a safer bet at this point)

---

### Post by iamjoe on 2012-07-13
I need help with this.  I have a fresh ubuntu installed on amazon and I need to remote into it.  I'm having trouble and need help.
Thanks

---

