---
title: "Problem with Karmic and vncviewer"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2009-10-28
Is anyone having a problem with vncviewer. For some time I have supported some friends using x11vnc. Because they have variable IP addresses and do not know how to port forward through a router I use the following scheme.

They have a launcher on the desktop which executes the following

```
x11vnc -noxdamage -connect <my ip address>
```

The above should connect using port 5500 to my system.

On my system I execute

```
vncviewer -listen
```

This has worked for sometime, until I upgraded my system to Karmic.
Now when I execute vncviewer I get

> peter@wilodesktop:~$ man vncviewer
peter@wilodesktop:~$ vncviewer -listen
vncviewer -listen: Listening on port 6524
vncviewer -listen: Command line errors are not reported until a connection comes in.


note its listening on 6524 ...... although the documentation says it should listen on 5500


Can anyone confirm this as a bug?

---

### Post by krunge on 2009-10-28
Which vncviewer is this? (i.e. flavor and version number)

Maybe try```
vncviewer -listen 0
vncviewer -listen :0
vncviewer -listen 5500

```
etc..

---

### Post by Peter09 on 2009-10-28
Thanks Krunge,

```
vncviewer -listen 0 
```

works. This is a change in Karmic though, as I have not needed to do this before.

---

### Post by krunge on 2009-10-28
> This is a change in Karmic though, as I have not needed to do this before.
Which viewer is this?  That may help explain what changed.  What does "vncviewer -h" reveal?  Do you have access to an earlier setup where "vncviewer -listen" still works?  If so, what does the -h print out for it?

---

### Post by Peter09 on 2009-10-28
> peter@toshlaptop:~$ vncviewer -h
TightVNC Viewer version 1.3.9


Sorry but I don't have a system which is not now Karmic. This behavior occurs on at least three of my machines.

---

### Post by krunge on 2009-10-29
> **Peter09 said:**
> Sorry but I don't have a system which is not now Karmic. This behavior occurs on at least three of my machines.
OK.  It seems like something added 1024 to 5500 to get the port 6524 yours listens on when supplying '-listen' with no number.  That may be a bug you want to report.

---

