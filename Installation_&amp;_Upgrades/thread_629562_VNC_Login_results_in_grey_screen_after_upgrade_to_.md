---
title: "VNC Login results in grey screen after upgrade to gutsy"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by bluegecko73 on 2007-12-02
When I ran Feisty I used to be able to connect via VNC to GDM and login to my headless pc, but since upgrading to Gutsy I just keep getting a grey chequered screen every time no matter what (I've also ran it on a non-headless pc that also worked before upgrading).
I can't find any log files that report a problem, or any advice I can follow to turn logging on so I've no idea where its failing - whether its a new security feature that's now enabled, a new setting or something that's crashing.
I originally followed the very helpful tutorial found [here]("http://ubuntuforums.org/showthread.php?t=42941&highlight=VNC+GDM") but I can't see any updates on that thread that suggest a cure for this problem.

Does anyone else have the same issue or know why this is occurring under Gutsy?
If you have a definite fix, that'll be even better.

Thanks in advance.

---

### Post by bluegecko73 on 2008-04-23
I finally found the answer to my problem in this thread [[COLOR="DarkRed"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=658643"), in the 3rd posting.

Turns out that instead of specifying > -query localhost in my inetd.conf or xinetd service arguments for my Xvnc, I needed to use > -query ::1 so that gdm talks to the connecting host instead of localhost, e.g. > server_args = -inetd :1 -desktop=MyServer [COLOR="Blue"]-query ::1[/COLOR] -geometry 1024x768 -IdleTimeout 7200 -depth 16 -fp /usr/share/fonts/X11/misc -once securitytypes=none -extension XFIXES 

After that quick change it all worked once again.

---

