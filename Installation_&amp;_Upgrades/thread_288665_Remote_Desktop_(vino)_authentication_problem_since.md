---
title: "Remote Desktop (vino) authentication problem since upgrade"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by apocralypse on 2006-10-30
I finally have my machine upgraded to Edgy, despite a few teething problems. This is the first problem I have have found so far and it's annoying because it prevents me logging in remotely with a GUI:

Symptoms:

 When I try to connect a vnc client to my machine I get a password prompt, when I enter the correct password I get "VNC authentication error". I cannot connect to VNC on my machine :(

Setup:

 This was working in Dapper, no longer works in Edgy. I am connecting through an SSH tunnel which is established correctly and if I telnet to 5900 through the tunnel I get "RFB 003.007" which is correct for vnc I believe.

 In the file ~/.gconf/desktop/gnome/remote_access/%gconf.xml under password there is a string. This string corresponds to the base64 encoding of my password which I believe is as it should be.

 I am connecting from Windows with TightVNC viewer using Putty to set up the SSH tunnel.


 ----

 Anyone know what this is going on here. It seems like very strange behavior. Any help appreciated.

-Kev-

---

### Post by apocralypse on 2006-10-30
Have I posted this in the correct forum?

-Kev-

---

### Post by jrasmussen0 on 2006-10-30
I'm getting the same error, but I think it has more to do with 3D acceleration and Xgl than VNC.

After upgrade, I was unable to connect with VNC.  After fiddling a bit, I was able to get it to work.  A day later, I noticed that my 3D acceleration for my ATI card was not enabled.  Since I enabled fglrx, I cannot get back into VNC.

Apparently the bug is fixed but maybe not committed.

[https://launchpad.net/distros/ubuntu/+source/vino/+bug/65795]("https://launchpad.net/distros/ubuntu/+source/vino/+bug/65795")

---

