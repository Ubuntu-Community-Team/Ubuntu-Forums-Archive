---
title: "VNC problems after Hardy upgrade"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by fridaythe14th on 2008-06-25
Been running VNC flawlessly before but since upgrading I have this problem:

My client (VNC Viewer on WinXP) closes itself. This happens when the server stops responding. It happened occationally before too, like when someone tripped over the network cables. Only now it happens a lot more often. One sure way to trigger it is by using the scrollbars, which I guess requires sending a lot of information, and watching a video-clip of course.

I tried using NX instead, but I get the exact same problem (only it says "connection closed" instead of shutting down), so I really don't think this is a VNC problem.

Please don't tell me to use SSH instead as I've seen in lots of VNC threads. It is not what I asked about.

---

### Post by Sawyer_ on 2008-06-25
Why not use SSH? For example NX uses SSH auth by default in its configuration.

For what comes to the problem with the connection getting closed, maybe check the system logs and VNC logs etc.

---

### Post by timcredible on 2008-06-25
why not use XDM?  it's on every linux and unix machine by default, and it works correctly (XDM is what you're using to login to your linux machine on the console now).  click on my sig for a how to.

---

### Post by fridaythe14th on 2008-06-25
Thank you :) I'll try that and see if I get similar problems.

> **Sawyer_ said:**
> Why not use SSH? For example NX uses SSH auth by default in its configuration.
I need gui access. I might be switching to NX if I get this working. I'm having the same problem there though, as mentioned. Security isn't a big issue as I've set up my firewall to deny everything except my laptop, which is on the same LAN (same with SSH, because of brute force paranoia).

> For what comes to the problem with the connection getting closed, maybe check the system logs and VNC logs etc.
I couldn't find any VNC logs at all. they're supposed to be in ~/.vnc or /var/logs/gdm but no. The NX server log file was empty.

---

