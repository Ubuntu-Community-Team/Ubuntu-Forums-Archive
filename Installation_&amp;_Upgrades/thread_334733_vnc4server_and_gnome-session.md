---
title: "vnc4server and gnome-session"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by RoboCuz on 2007-01-09
I had been using vnc4server to start a vncserver, and I had been using -query localhost -once as options, and using the gnome-session to start up my login session.  This had all been working just fine, and then a couple of days ago, there was an update pushed out, for vcn4server from 
4.1.1+xorg1.0.2-0ubuntu1 to 
4.1.1+xorg1.0.2-0ubuntu1.6.10.1

this caused my gnome-session to start tossing errors on startup, and in .xsession-errors:

Xsession: X session started for rich at Tue Jan  9 10:57:23 EST 2007
The program 'x-session-manager' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 74 error_code 1 request_code 146 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Once I downgraded vnc4server to the original, everything worked.

Even to get this far, I believe I had to do a dpkg-reconfigure on gnome-session or vnc4server, I forget exactly (sorry).  That seemed, I recall, to get me farther then I was before, but I still had to down-grade in the end.

I hope someone can tell me why I can't use gnome-session with the newest vnc4server, but at least for now I am working again.

$Rich

---

### Post by RoboCuz on 2007-01-14
I believe the problem has been identified as Bug #78282 [here]("https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/78282") and also discussed as bug 78294 [here]("https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/78294").

There does not seem to be a solution yet, but it has been identified by a few people. It looks like it is related to a new build of vnc4server, not the security fixes that have just been added.

$Rich

---

