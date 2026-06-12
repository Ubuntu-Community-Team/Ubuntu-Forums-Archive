---
title: "[SOLVED] Open Arena Issue"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by craggsy on 2008-10-08
Ok sorry for the title but it's the only thing i've tested.

I have an aspire one and when I was running 8.04 OA and other games worked fine. Now I start up go to play OA and screen goes black for a split second then, just goes back to the desktop. However my cursor is frozen so I have to ctrl alt del and log out. I log in try it again, sometimes I works on the second login others on the third.

I am getting an "x11 initialization failed" error, though I don't understand why it works after I log in again.

> Oct  9 00:44:18 adam-netbook gdm[6970]: pam_unix(gdm:session): session closed for user adam
Oct  9 00:44:44 adam-netbook gdm[6970]: pam_unix(gdm:session): session opened for user adam by (uid=0)
Oct  9 00:44:44 adam-netbook gdm[6970]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Oct  9 00:44:44 adam-netbook gdm[6970]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Oct  9 00:44:44 adam-netbook gdm[6970]: Autolaunch error: X11 initialization failed.
Oct  9 00:44:44 adam-netbook gdm[6970]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Oct  9 00:44:44 adam-netbook gdm[6970]: Autolaunch error: X11 initialization failed.
Oct  9 00:44:44 adam-netbook gdm[6970]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Oct  9 00:44:44 adam-netbook gdm[6970]: Autolaunch error: X11 initialization failed.
Oct  9 00:44:44 adam-netbook gdm[6970]: )
Oct  9 00:50:01 adam-netbook CRON[9687]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct  9 00:50:01 adam-netbook CRON[9687]: pam_unix(cron:session): session closed for user root

Thats the error I get, any ideas on how to fix this ? 

Cheers

Adam :KS

---

### Post by kforum on 2008-10-08
in all accounts, even if it has nothing to do with you, check this:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/159263](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/159263)
(the --important-- part i mean)

on to you, 
are you trying to connect online?
ive seen similar problems with Nexuiz before, but there where all screen resolution issues(which where derived form config file issues).

on a further note whats your xorg-server version/your video card?
or generally more info about your problem would be good.


cheers.

---

### Post by craggsy on 2008-10-08
> **kforum said:**
> in all accounts, even if it has nothing to do with you, check this:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/159263](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/159263)
(the --important-- part i mean)

on to you, 
are you trying to connect online?
ive seen similar problems with Nexuiz before, but there where all screen resolution issues(which where derived form config file issues).

on a further note whats your xorg-server version/your video card?
or generally more info about your problem would be good.


cheers.

I tried the fix you mentioned didn't help. Graphics are Intel 945GMA, it defiantly works as OA ran in 8.04. xserver-xorg-video-intel 2:2.4.1-1ubuntu6 (latest version)

I'm not really sure what else to say, game looks like it is going to load but instead of the intro you get taken back to the desktop, and the cursor is stuck, so I can't click anything. All the keyboard shortcuts still work though.

I know a little bit about ubuntu and i've never had this issue before, it only seems to be Open Arena the other games I've tested (glest warzone 2100).

The open gl info is as follows (from glest)
Version 1.4 Mesa 7.2
Renderer: Mesa DRI Intel 945GME 20061102 x86/MMX/SSE2
vendor: Tungsten Graphics Inc
Max lights : 8
Max texture sizze: 2048
Max texture units: 8

Both OpenArena and Glest run Open GL, though Glest launches everytime OA only randomly. I ran System Monitor after OA "crashed" and OA wasn't running so I guess it's just not launching :confused:

Hope this info can help

Adam

---

### Post by craggsy on 2008-10-08
I found the problem, I followed the steps in [Pulse Audio fix thread]("http://ubuntuforums.org/showthread.php?t=866965") and now it all works perfectly. 


> ------ Initializing Sound ------
Loading "libopenal.so.0"...
Failed to load library: "libopenal.so.0".
SDL_Init( SDL_INIT_AUDIO )... OK
SDL audio driver is "alsa".
ALSA lib pcm_pulse.c:629:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

E: stream.c: Assertion 's' failed at pulse/stream.c:971, function pa_stream_drain(). Aborting.
Aborted (core dumped)


---

### Post by kforum on 2008-10-08
great!

---

### Post by craggsy on 2008-10-09
Cheers for you help, for some reason when I removed -quiet from the launcher to start with it didn't display what was happening in terminal, once it did that it was sorted :guitar:

---

