---
title: "XDMCP on 11.04"
date: 2011-06-20
forum: Installation &amp; Upgrades
---

### Post by theodore.lizard@gmail.com on 2011-06-20
New to forum, didn't see this posted already, sorry if I missed it (or search missed it).

I'm on a private network and would like to have XDMCP turned on so different users can access the system with a greeter and log in to their own desktop.

I've edited /etc/gdm/custom.conf to include
[xdmcp]
Enable=true

and I've restarted the entire system.

To test if this works, I've tried 'Xnest :1 -query localhost' - which on other _nix systems will bring up the greeter, then I know that all I have to do is deal with firewall issues, etc. On Ubuntu 11.04 I just get a blank screen.

I've seen others asking for help with XDMCP, and the answers are to use VNC, which from my experience allows you to _share_ the current desktop, not create a new one for a different user to use at the same time. If I am mistaken please let me know.

So, any ideas on how to get XDMCP up and running on Ubuntu 11.04?

Thanks

---

### Post by davre1 on 2011-07-09
Hi 
 
I am also struggling to set up XDMCP on 11.04 Xbuntu with Xfce. Most tutorials advise setting RemoteGreeter=/usr/lib/gdm/gdmlogin, but I do not have gdmlogin in my /usr/lib directory.
 
Any help on how to setup and debug initially on local machine gratefully received.

---

