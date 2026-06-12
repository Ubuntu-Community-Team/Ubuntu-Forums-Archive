---
title: "VLC Classic Mode Gone?"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sddfdds on 2008-10-13
Is anyone else unable to use vlc 0.9.4 in classic mode.  I have it set to classic mode with the video integrated into the interface, but no matter what, a separate window for the video always opens.

---

### Post by FuturePilot on 2008-10-13
I've noticed this too. It's very odd and annoying. :(

---

### Post by jfernyhough on 2008-10-13
Mine works as normal...

Try deleting your VLC settings:

$ cd ~
$ rm -fR .vlc

When it's next opened VLC will recreate the defaults.

---

### Post by taavikko on 2008-10-13
Confirmed, thus created appropriate report, feel free to chip in :)
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/282582](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/282582)

---

### Post by Hallavej on 2008-10-13
And in addition "Show a controller in fullscreen" does not work and I can no longer save streams in a file. 0.9.4 introduces more bugs than it solves in my opinion.:(

---

### Post by FuturePilot on 2008-10-13
Apparently this is some sort of workaround for another bug.

[http://forum.videolan.org/viewtopic.php?f=13&t=51032&start=0&st=0&sk=t&sd=a]("http://forum.videolan.org/viewtopic.php?f=13&t=51032&start=0&st=0&sk=t&sd=a")

[https://trac.videolan.org/vlc/ticket/2136]("https://trac.videolan.org/vlc/ticket/2136")

---

### Post by Kow on 2008-10-14
VideoLan needs to stop being so sneaky about disabling features with no information being conveyed to the user.

---

### Post by FuturePilot on 2008-10-16
Fixed in the latest updates :)

---

