---
title: "Gnome-keyring-daemon error after clean install 8.10"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by lamppis on 2008-10-31
What does this mean and how shall I fix it?


      : gnome-keyring-daemon: couldn't lookup keyring component setting:. (Lisätiedot  Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified

      : Autolaunch error: X11 initialization failed.

      : )gnome-keyring-daemon: couldn't lookup ssh component setting: (Lisätiedot -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified

       Autolaunch error: X11 initialization failed.

       )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
   
       Autolaunch error: X11 initialization failed.

---

### Post by wdanda on 2008-11-07
I'm having a similar issue when I updated from 8.04 to 8.10... My system was working great until I installed 8.10 and rebooted... Now I can't get passed after the GDM login page... Once I inform the credentials and click on the login button, the x screen gets refreshed but gnome won't load... I'm stuck with an empty window...

Going to the root console, I could manage to see a weird message in the auth.log file. Here it is:

```

Nov  5 22:59:55 pantro gdm[7838]: pam_unix(gdm:session): session opened for user pantro by (uid=0)
Nov  5 22:59:55 pantro gdm[7838]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Nov  5 22:59:55 pantro gdm[7838]:** gnome-keyring-daemon: couldn't lookup keyring component setting**:** Failed to contact configuration server**; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: **Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified**
Nov  5 22:59:55 pantro gdm[7838]: **Autolaunch error: X11 initialization failed.**
Nov  5 22:59:55 pantro gdm[7838]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Nov  5 22:59:55 pantro gdm[7838]: Autolaunch error: X11 initialization failed.
Nov  5 22:59:55 pantro gdm[7838]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Nov  5 22:59:55 pantro gdm[7838]: Autolaunch error: X11 initialization failed.
Nov  5 22:59:55 pantro gdm[7838]: )

```

I didn't notice any helpful message in the syslog. 

Below are relevant details my environment:

- AMD 64bit processor
- Two monitors (which I though it was the cause of my issue, so I rebooted in the recovery mode and tried to fix the X server. That didn't fix the problem)
- Nvidia card (I was using nvidia's proprietary drivers)
- Wireless network card (that always worked fine, I'm not using any proprietary software)
- Wireless Network configured with WPA ('tsk' mode I think, will double check)

So, I'm two days now without my ubuntu and I'm getting impatient... If this is not "fixable", I'm willing to reinstall Ubuntu from a liveCD, but without deleting all my personal stuff... 

Hope you guys have any clue on what might be happening...

Thanks,
Wagner

---

### Post by umatchan on 2008-12-28
Exact same problem - PLEASE HELP!!!

---

### Post by patmalcolm91 on 2009-01-11
I'm also having this problem.

---

### Post by harshl on 2009-03-10
I am also having this exact same problem, only mine presented after running updates on mythbuntu 8.10.

Anyone have any ideas?

Thanks,
-Landon

---

### Post by modctek on 2009-03-10
I'll pile on with a "me too" post. I'm using NoMachines NX Client to log into this machine from other workstations, so perhaps that's part of this problem? Occasionally, I experience what appears to be stale NX sessions that instead of being able to reconnect, I have to delete/terminate the old sessions.

```
Mar  9 21:29:13 northstar2 gdm[5684]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Mar  9 21:29:14 northstar2 gdm[5684]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar  9 21:29:14 northstar2 gdm[5684]: Autolaunch error: X11 initialization failed.
Mar  9 21:29:14 northstar2 gdm[5684]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar  9 21:29:14 northstar2 gdm[5684]: Autolaunch error: X11 initialization failed.
Mar  9 21:29:14 northstar2 gdm[5684]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Mar  9 21:29:14 northstar2 gdm[5684]: Autolaunch error: X11 initialization failed.
Mar  9 21:29:14 northstar2 gdm[5684]: )
Mar  9 21:29:14 northstar2 x-session-manager[1679]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
```

---

### Post by modctek on 2009-03-10
Answered my own question with a little Googling. Short answer is: it's a bug that should be fixed shortly.

[http://bugzilla.gnome.org/show_bug.cgi?id=558181](http://bugzilla.gnome.org/show_bug.cgi?id=558181)

---

### Post by Guus1982 on 2009-03-22
the bug should be fixed shortly? the first post is from 31 october. Really sure some1 didnt fixed this already?

---

### Post by Spectre5 on 2009-03-26
I have this same problem...

---

