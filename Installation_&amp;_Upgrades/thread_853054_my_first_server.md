---
title: "my first server"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by simon_wrafter on 2008-07-08
Hi, 

I was thinking of setting up a small file server just to see what I can do with ubuntu and linux. 

The computer is an old Pentium III @ 650 MHz with 265 MB ram. It's recently been installed with Xubuntu which I was thinking might be able to pose as a server. But recently I've been thinking maybe I should install Ubuntu Server? The bios is from 1999 which poses as a problem when trying to install ubuntu, due to bios cut off or what ever it's called, I hav not been able to find a new version of the bios.

In either case, what software should I install? How should I configure the computer in other respects?

Also I'm lacking a screen for the computer, I can get one from my brother, but if it's possible I'd prefere to make some sort of connection to the computer through my laptop and run an installation that way... But don't let this "feature" hinder you from telling me to do a fresh install of Server even if it isn't possible, it's not such a big problem.

So, my questions are:
1. Xubuntu / Ubuntu Server??
2. Software to install?
3. Other necessary setups?

and please bear with me, for I am but a learner nad this is my first post in an Ubuntu forum. If there's any thing other you would like to know feel free to ask.

//Simon

---

### Post by AndyCooll on 2008-07-08
It depends on your level of confidence. 

If you can use the command line then running a file server doesn't need a gui interface and you'd choose Ubuntu Server. You then wouldn't need a screen, you'd access your server from your laptop via SSH.  

I've not done this for awhile. IIRC you'll probably want to install openssh-server, nfs-common (and the server end to it, I can't remember if this is installed by default on Ubuntu Server) and Samba if you'll want Windows pc's to access the server.

Configuring the above would be all you'd need to get you going.

:cool:

---

### Post by simon_wrafter on 2008-07-09
Ok, thanks. I think I'll go with the Server installation. Do I need to install some programs on my laptop for this?

---

