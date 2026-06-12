---
title: "gutsy gnome settings daemon"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by trash on 2007-10-21
fresh install on an ibook g3 900, cd is good and I have few other problems, sound is one but may be an alsa issue. After booting up I always get this message..

'There was and error starting the Gnome settings daemon Some things such as themes,
sounds, or backgroung settings may not work correctly. The settings daemon restarted too many times. GNOME will try to restart the Settings Daemon next time you log in.'

I haven't found a fix or many other people who have this problem on gutsy so anybody have a suggestion?

---

### Post by igor_av on 2007-10-22
> **trash said:**
> fresh install on an ibook g3 900, cd is good and I have few other problems, sound is one but may be an alsa issue. After booting up I always get this message..

'There was and error starting the Gnome settings daemon Some things such as themes,
sounds, or backgroung settings may not work correctly. The settings daemon restarted too many times. GNOME will try to restart the Settings Daemon next time you log in.'

I haven't found a fix or many other people who have this problem on gutsy so anybody have a suggestion?

I have the same problem (on a 900 mhz g3 iBook too). I'm still looking for a solution... Meanwhile, I use XFCE instead of Gnome...

---

### Post by trash on 2007-10-22
Ya i was just giving gnome another chance but I think it's back to XFCE for me too, soooo glad to hear it's workin nice for you:)

---

### Post by trash on 2007-10-22
> **igor_av said:**
> I have the same problem (on a 900 mhz g3 iBook too). I'm still looking for a solution... Meanwhile, I use XFCE instead of Gnome...


Hmm does sound work for you? I can't even get the volume control to load.

---

### Post by Samhain13 on 2007-10-23
Hi, I've been experiencing the same thing-- occasionally.
It takes me a couple of X restarts until it goes away, so I thought to just wait a few more seconds before logging-in to perhaps give the Daemon a chance to load. This seems to be working. Err,,, but then again, I'm just another noob.

[edit]
Nope. I still get the error message occasionally.

---

### Post by funkythumb on 2007-10-23
Just downloaded a fresh copy of Ubuntu Studio today, verified the disk, installed on Dell D600, went through all the updates, and after a couple of hours, a new batch of updates appeared. Tried to install (I use Aptitude for all my updates & installs whenever possible) and it gave me a message RE: unable to install plug-in updates for Audacious. Used the Update Manager, unchecked the Audacious updates and the rest downloaded and installed OK.

After restart, now I get message RE: Gnome settings daemon. Given the posts before mine, looks like it's a Gutsy issue more than an Ubuntu Studio one. :(

---

### Post by JBAlaska on 2007-10-23
This is a known bug with the Audacious update (that should have been fixed by now) both the Audacious update and the audacious plugins have the same file in them.
Removing and reinstalling the above through synaptic should cure the problem.

---

### Post by trash on 2007-10-23
I decided to remove gnome and stick with xfce... yay no more errors LOL

---

### Post by k49 on 2007-10-25
I just upgraded to 7.10/Gutsy and had the same problem. It was not fixed by logging out and logging back in again (oddly, after I click "Quit" the shutdown/restart/logout box takes a *very* long time to appear). When I tried starting gnome-settings daemon manually from a virtual console (i.e. what you get from pressing control-alt-F1), I got the following error message:
```
(gnome-settings-daemon:21635): Gtk-WARNING **: cannot open display:
```

When I tried starting it manually from gnome-terminal, I got:
```
[1193269257,000,xklavier.c:xkl_engine_start_listen/]    The backend does not require manual layout management - but it is provided by the application[1193269257,000,xklavier.c:xkl_engine_start_listen/]   The backend does not require manual layout management - but it is provided by the applicationCould not initialize GStreamer: Error re-scanning registry , child terminated by signal
```

I don't know what any of this means, but I figure it might help someone figure it out what's happening.

---

### Post by Samhain13 on 2007-10-25
Humm... I don't have Audacious and Audacious plug-ins. But I still get the error occasionally... I wonder...

[edit]
I found a few things here: [https://launchpad.net/ubuntu/+source/control-center/+bug/61381](https://launchpad.net/ubuntu/+source/control-center/+bug/61381)
The "disable ESD from Sound Preferences" seems to be working for me. But I don't think it's an over-all solution, based on the discussions in Launchpad.

---

### Post by funkythumb on 2007-10-29
AUDACIOUS PLUGIN ERROR UPDATE:

Today a re-ran the update, and this time no error appeared and the updates were applied correctly. Unfortunately, still getting the Gnome-settings error.

---

### Post by stitch on 2007-10-30
Hi, same error for me, occasionally I have this warning.
My graphic card is an ATI Radeon 9550SE.

Ciao/Stitch

---

### Post by igor_av on 2007-10-31
> **trash said:**
> Hmm does sound work for you? I can't even get the volume control to load.

Sound doesn't work for me. I think I'll downgrade to 7.04 for a while...

---

### Post by MWRMWR on 2008-03-29
> **trash said:**
> I decided to remove gnome and stick with xfce... yay no more errors LOL

I just updated my GG system for Movie Player and a huge bunch of other things :-{ and fell down this hole.

I bet it's really simple to get into recovery mode (I can do that) and than replace gnome with anything else..

unfortunately I don't know that spell :(

Please make my life (and anyone else that has googled here) easier by actually describing the necessary incantation; until then, it's back to Gatesware again as I have a stable GutsyGibbon install image with ATI drivers installed but can never progress to a usable system.

thanks, Mark
#-o

p.s. anyone know where to find the error logs there are bound to be for this issue ?
p.p.s. Dear Mr Ubuntu, this behaviour has been kicking around for several years now and it appears
that triggers for it get fixed from time to time; the really annoying problem is that it is impossible
to log in via the GUI when this popup occurs.

---

### Post by trash on 2008-03-29
Sorry to say but the boot problem with Gutsy killed my G3 after many many reboots trying to fix it... so I went and bought an x86.

> **MWRMWR said:**
> I just updated my GG system for Movie Player and a huge bunch of other things :-{ and fell down this hole.

I bet it's really simple to get into recovery mode (I can do that) and than replace gnome with anything else..

unfortunately I don't know that spell :(

Please make my life (and anyone else that has googled here) easier by actually describing the necessary incantation; until then, it's back to Gatesware again as I have a stable GutsyGibbon install image with ATI drivers installed but can never progress to a usable system.

thanks, Mark
#-o

p.s. anyone know where to find the error logs there are bound to be for this issue ?
p.p.s. Dear Mr Ubuntu, this behaviour has been kicking around for several years now and it appears
that triggers for it get fixed from time to time; the really annoying problem is that it is impossible
to log in via the GUI when this popup occurs.

---

### Post by nairatinu on 2008-04-01
I log off and back on, which is a pain but works.  do you notice if the log off icon is the green "running man" when this error occurs (instead of the "door")?

---

