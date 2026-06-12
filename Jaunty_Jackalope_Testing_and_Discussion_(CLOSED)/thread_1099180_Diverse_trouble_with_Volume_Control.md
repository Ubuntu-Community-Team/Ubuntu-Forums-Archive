---
title: "Diverse trouble with Volume Control"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Florob on 2009-03-17
Hi everybody,
I'm having some rather strange problems with controlling my volume, which actually feel like separate issues, but I suspect are somehow entangled.

1. I can't get any volume control applet to show up. Adding one to the Panel doesn't seem to do anything. I should add that it doesn't work no matter if pulseaudio is running or not (I tend to uninstall it because it uses a lot of CPU on my system, which according to the pulseaudio devs is impossible, but still the case :( ).

2. Something seems to go wrong once I use my multimedia keys to control the volume. I can control the volume once and the notification-ish thing pop's up. While that "notification" is there turning up and down the volume works just fine. Once it is gone I can no longer use the multimedia keys (making it impossible to control the volume if not using alsamixer).
This is especially frustrating because some applications are rather allergic to this. E.g. Sonata tells me:
"ERROR:dbus.proxies:Introspect error on :1.10:/org/gnome/SettingsDaemon/MediaKeys: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."
Totem takes ages to start playing a video and evince becomes unbearably slow (I'm not really sure the evince thing is related though).

3. I can't open the audio preferences. When I try to nothing happens at all.

I'd really like to file bug's about those, but somehow "It doesn't work" doesn't seem like a good bug description and I'd suspect that I'm not the only person with those problems, yet I have found none of those in LP.

Any ideas?

---

### Post by Bastanteroma on 2009-03-18
Similar issues here. No audio control shows up by default in my panel and adding one doesn't make it appear.

---

### Post by kj74 on 2009-03-18
I taught i was only one with this problem. Any change you have CA0106 chip? This must be hardware specific bug. This happens with live cd as well so no easy fix. Reinstalling doesn't help. New pulseaudio volume control works and you can ofcourse use alsamixer.

---

### Post by Florob on 2009-03-18
I actually highly doubt it's hardware specific (FWIW I have a ICE1712).
Can you tell me how to start the pulseaudio based volume control?

---

### Post by kj74 on 2009-03-18
You have to install it first and remove the old one because it's still  going to cause problems. New one is called "gnome-volume-control-pulse". ICE...intresting, you're going to have problems with glitch-free pulseaudio.

If this doesn't get fixed, Jaunty is going to be most broken Ubuntu release for me.

---

### Post by Florob on 2009-03-18
Hmm... interesting. I can't find any packages containing a gnome-volume-control-pulse, nor any packages that sound like they'd contain such a thing.

As for having problems with glitch-free this is really one of my lesser concerns when it comes to pulseaudio. I have had my share of problems with it even before glitch-free existed. Most notably the fact that throughout every release it has been taking at least 10% of my CPU (AMD AthlonXP 2800+ I do not really consider that "too old"...).

---

### Post by kj74 on 2009-03-18
I guess it's not yet on mirror you're using. [https://lists.ubuntu.com/archives/jaunty-changes/2009-March/007683.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-March/007683.html)

---

### Post by Florob on 2009-03-18
Indeed.
It is now and YAY! I finally have a GUI (if you count alsamixer as CLI) way to control my volume again. But at the cost of using pulseaudio.
I hope they fix the bugs for the release...

---

### Post by rockin_goliath on 2009-03-25
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/348417]("https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/348417")

I just filed a bug against gnome-volume-control-pulse. Please help prepare this really great audio tool for the final release by submitting your information to the bug report.

---

