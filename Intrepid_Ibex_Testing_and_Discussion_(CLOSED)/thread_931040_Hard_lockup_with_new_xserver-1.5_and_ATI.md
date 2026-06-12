---
title: "Hard lockup with new xserver-1.5 and ATI"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dkasak on 2008-09-26
Hi all.

I've reported this issue already in the Xorg mailing lists, but no-one there is really biting ( * see below ), so I'll give it a go here.

I have an AMD Turion notebook, with a Radeon X700 Mobility. I'm running 64bit Intrepid, updated to current. I used to run Gentoo for the past 5 years or so, and my Radeon has been rock solid for years.

Now, X locks HARD ( no magic system request keys work ) when starting up. With the default xorg.conf which uses XAA, I get a corrupted GDM display, and a hard lockup. The screen looks like:
[http://entropy.homelinux.org/gdm_xaa.jpg]("http://entropy.homelinux.org/gdm_xaa.jpg")

If I enable EXA ( which I've been using since the zero-copy-texture-from-pixmap stuff landed ), I get a black screen with a crosshair cursor.

In both cases, I can mouse the mouse pointer VERY slowly, but have to hard-reset my laptop :(

Logs:
[http://entropy.homelinux.org/Xorg_exa.0.log]("http://entropy.homelinux.org/Xorg_exa.0.log") - note that I made this log a couple of days ago
[http://entropy.homelinux.org/Xorg_xaa.0.log]("http://entropy.homelinux.org/Xorg_xaa.0.log") - this one I did this morning, after a complete re-install and update last night. I thought I had it fixed last night - I rebooted after the update and everything seemed OK - compiz running fine etc, but this morning ... back to lockups.

If I disable DRI ( via the line 'Option "DRI" "0"' ), then X starts ***every*** time. Otherwise I can get into it about 1 in 20 times - the rest of the time it locks. It's infuriating.

The only response / questions I've gotten so far from a developer are asking if I use PAT in my kernel ( which apparently I don't ... I'm using whatever kernel Intrepid provides at the moment, but I suppose I should try building my own and seeing if that's the issue ), and what DRM I'm using. I responded to these and haven't heard back.

Help!

---

### Post by MALEADt on 2008-09-27
Sorry, can't comment or confirm this bug. I have been having some sporadic X-lockups too (in combination with EXA & ATI driver), but Xorg.log only indicated a backtrace log, and no infinite loop as your log does.

Anyhow, you could throw the same question in a more active channel, like on IRC: #radeon @ FreeNode?

---

### Post by Robertjm on 2008-09-27
Unfortunately I can confirm locking up :(

I upgraded XORG and now I get an error about running in low graphics mode and asking me how to proceed but by that time it's too late and it's a hard lockup.

Using Radeon X1600 AGP card

---

### Post by UbuWu on 2008-09-27
Did you file a bug or look for existing bug reports in Launchpad?

---

### Post by Robertjm on 2008-09-27
For me it turned out it was only X that was hard locked, which in turn locked the mouse and couldn't let me choose any of the key options there.

However, I found I was able to Ctl-Alt-f1 and get to the command line. After that I ran an apt-get update/upgrade. AFter restarting I had a GDM, however, no keyboard and mouse (which is a bug that's been reported).

After editing the xorg.conf to add the keyboard and mouse sections that were left out, I'm able to get into Gnome now.

---

### Post by kesman on 2008-09-29
With 32-bit Intrepid Alpha 6 and an Acer 5021 with the same, 64-bit turion processor and a X700 I have no problems, other than fglrx not working, but this is quite obvious since it doesn't support Xorg 7.5 yet afaik.

---

### Post by PGHammer on 2008-09-29
> **Robertjm said:**
> Unfortunately I can confirm locking up :(

I upgraded XORG and now I get an error about running in low graphics mode and asking me how to proceed but by that time it's too late and it's a hard lockup.

Using Radeon X1600 AGP card

Sorry; I *cannot* confirm the bug (I also have the Radeon x1650 AGP card).
I have two other issues; however, I suspect that both are due to non-XORG issues.  (First off, the lack-of-screen-resolutions issue is due to poor EDID data from the monitor itself, and affects every distribution of Linux I've used and even affects Windows; the inability to get those resolutions back is due to displayconfig-gtk being deprecated/missing in Intrepid A6 (which is what I'm running).)

---

### Post by MALEADt on 2008-09-29
@Robertjm:
Does your Xorg.0.log (or the "old" version) contain traces of a "backtrace" after having X crashed? If so, the crash you're experiencing might be related to the one I have come across. It didn't come together with a failsafe GDM session though, but those could be unrelated.

---

### Post by MALEADt on 2008-09-30
```
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
```

Affirmative. [Launchpad entry created](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/276518), please ACK.

---

