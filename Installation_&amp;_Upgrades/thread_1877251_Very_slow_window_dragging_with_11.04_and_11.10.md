---
title: "Very slow window dragging with 11.04 and 11.10"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by ljp37 on 2011-11-07
Anyone know what could be causing horrible slowness while dragging windows in 11.10?  This also happened on 11.04 for me.

See video:

[http://youtu.be/SV5pbQ8P3Ng]("http://youtu.be/SV5pbQ8P3Ng")

Using Unity with default compiz settings. Other graphical effects work fine.  The weird thing is that for about 30 seconds after first booting into X, window dragging is very smooth... and then this lurching starts.

I was originally using an ATI video card, but I switched to nVidia hoping to fix this.  No luck --- it does not seem to be specific to the GPU.  It occurs with both the open-source and proprietary drivers, for both ATI and nVidia.

Despite what it looks like on the video, the computer is not thrashing. There's plenty of available memory and CPU.  Other tasks (i.e. playing a video in another window) are unaffected by whatever is causing this lag. 


System specs:
* Ubuntu 11.10
* AMD Phenom x6 1045T
* 8 GB RAM
* nVidia GT 240  (also tried with Radeon HD 5450)

---

### Post by ljp37 on 2011-11-11
(follow up)

I posted this here and on Ask Ubuntu, and nobody seems to know.  One poster on YouTube also has the same problem.

I've since switched to the Ubuntu 2D session, since it is not affected by this bug.

---

### Post by danzvash on 2011-11-13
I've been hit by this too. 

There should be no need for a workaround for something so basic as moving windows.

Goodbye Unity, hello KDE4.

---

### Post by gshegosh on 2011-11-22
Just a "me too" post from me, so I get notification if anyone knows how to fix it.

I really wanted to give Unity a try, but if I can't move windows on an Intel i7 with 12G of RAM and decent graphics card (NVidia)...

---

### Post by ronniew on 2011-12-03
The bug is with windows decorations.... if you go into compiz and uncheck it then recheck it the windows go back to being able to be moved as normal.... like when you first startup.... over time the windows become choppy when moving..

my guess a memory leak somewhere.... 

hope it helps everyone... as temp fix and the developers as a spot to look at.

---

### Post by Traktion on 2011-12-15
A good temporary fix is to restart compiz:

compiz --replace

That seems to fix mine anyway. Compiz memory usage fell from about 350mb to 80mb too. Methinks there is a memory leak in there somewhere!

---

### Post by jvcastle on 2012-01-03
EXACTLY the same problem as ljp37 - right down to it working for about the first 30 seconds.  11.04 worked ok as did the early release, prior to some updates of 11.10  I tried ALL the recommended fixes - updated (as well as very old) nvidia drivers, used other desktop managers besides Unity etc.  No solution.  Something is broken in 11.10

Did a fresh install of 10.04 and will probably STAY there.

---

### Post by travlemon on 2012-02-02
> **danzvash said:**
> I've been hit by this too. 

There should be no need for a workaround for something so basic as moving windows.

Goodbye Unity, hello KDE4.


I totally agree!  My gaming laptop is a little on the old side now, but still handles video really well.  It certainly has the power to handle dragging a window around.

With that said, I doubt this will even get fixed on 11.10.  12.04 is due for release in April or so.  Being an LTS release, the fixes will probably be concentrated in 12.04.

I don't know anything about how Ubuntu addresses updates, I am simply going on an uneducated hunch!

---

