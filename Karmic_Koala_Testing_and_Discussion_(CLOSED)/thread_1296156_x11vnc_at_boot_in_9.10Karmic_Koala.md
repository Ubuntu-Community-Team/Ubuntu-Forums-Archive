---
title: "x11vnc at boot in 9.10/Karmic Koala"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by can2002 on 2009-10-20
Hi all,

I've been trying out the Karmic beta and have encountered an issue with running x11vnc via GDM.

I'd previously used the techniques shown elsewhere on these forums of editing the /etc/gdm/Init/Default file and then adding 'KillInitClients=false' in /etc/gdm/gdm.conf-custom.

Having discovered the new version of GDM in Karmic uses a new config file convention, I came across this article on the Gnome site:

[http://projects.gnome.org/gdm/docs/2.24/configuration.html#daemonconfig](http://projects.gnome.org/gdm/docs/2.24/configuration.html#daemonconfig)

Basically the old gdm.conf-custom entries now need to go into /etc/gdm/custom.conf; however it appears that the 'KillInitClients' option is no longer valid.

I thought I'd post this here in case anyone else tries to achieve the same.

Chris

---

### Post by krunge on 2009-10-20
> **can2002 said:**
> 
Having discovered the new version of GDM in Karmic uses a new config file convention, I came across this article on the Gnome site:

[http://projects.gnome.org/gdm/docs/2.24/configuration.html#daemonconfig](http://projects.gnome.org/gdm/docs/2.24/configuration.html#daemonconfig)

Basically the old gdm.conf-custom entries now need to go into /etc/gdm/custom.conf; however it appears that the 'KillInitClients' option is no longer valid.
Ah, this is sad.  So now instead of being hard for users to learn about KillInitClients and which file(s) they need to put it in, they can't change the behavior at all!

If you have x11vnc 0.9.6 or later, you can try the "-reopen" option:
[INDENT][http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-reopen](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-reopen)[/INDENT]
The -reopen mechanism is not as good as getting rid of the problem with KillInitClients, but is seems with the new GDM behavior there is not much else one can do short of having x11vnc restart (e.g. -loop or shell script) and then reconnecting the VNC viewer...

---

### Post by bodhi.zazen on 2009-10-20
Lots of changes with GDM, big loss of options in terms of configuration.

---

### Post by krunge on 2009-10-21
I believe I found an interesting way to work around this problem.

It appears that the display manager (i.e. GDM) cannot kill an initial client if the client doesn't have a window (either mapped or unmapped.) GDM evidently does an XQueryTree() to find all windows and kills their owners via XKillClient().

x11vnc creates a hidden 1x1 window for use with exchanging the clipboard selection, etc. This window leads to GDM killing x11vnc. So all x11vnc has to do is avoid creating that hidden window until it thinks the display manager login is finished.

I've uploaded an x11vnc 0.9.9 tarball that implements heuristics to delay the creation of that window:

[INDENT][http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9.tar.gz](http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9.tar.gz)[/INDENT]

I've tested it out on ubuntu 9.04 and it works pretty well.  I'd appreciate it if you could try it out on 9.10 and let me know how it goes.

It should work by default.  If it doesn't you can jack up the number of seconds it waits until after the first VNC client connects to when it tries to create the window, e.g.
```
x11vnc -env X11VNC_AVOID_WINDOWS=120 ...
```
will wait 2 minutes, so you have that long to log in via the GDM greeter.



**UPDATE:**

I posted an update to the ubuntu 9.10 GDM killing x11vnc in post #5 here:
[INDENT][http://ubuntuforums.org/showthread.php?t=1306696](http://ubuntuforums.org/showthread.php?t=1306696)[/INDENT]
it seems to work fine now.

---

### Post by can2002 on 2009-10-22
Hi there,

I've taken a slightly different approach myself - not applicable in many cases I realise, but in case it's of interest...

I've configured auto-login and then enabled the 'remote-desktop' option in 'System->Preferences->Remote Desktop' and selected the option to allow access and control.  I also specified the option to require a password.

In my case, the box is a combined MythTV-Backend/Asterisk server stashed in my loft, so I'm not concerned about physical access.

Cheers for the other responses too!
Chris

---

### Post by GoMad on 2009-10-22
Hi,
 
I'm a bit new to this, playing around with VNC and got it to startup but as you say when you login a user it restart x11vnc, I have added the option for the window wait and it has not worked for me - stop vnc starting on boot now.
 
So, can you explain what you have done exactly as it sounds very much a suitable solution ?   I am not worried about security etc, but I can not even find remote desktop option on 9.10 !
 
Thanks
 
GoMad.

---

