---
title: "Has Pulseaudio Latency Problems been fixed in Karmic ?"
date: 2009-09-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cdahmedeh on 2009-09-27
Hello,

I'm not running Karmic on my production machine. However, I would like to know if the Latency Problem has been fixed with PulseAudio in Karmic. In my current installation of Jaunty, I remove the pulseaudio package and the latency problem is fixed. When I am talking about latency, I'm talking about the sound that is heard 300-400 milliseconds after the event happens. This is mostly visible in games, such as Secret Maryo Chronicles, where let's the character jumps, you hear the sound 300-400 milliseconds after it happens.

Thanks

---

### Post by TrueTom on 2009-09-27
Have you tried the SDL PulseAudio plugin?

---

### Post by Psy[H[] on 2009-10-03
Latency is still there. 
And more: removing pulseaudio now breaks sound control. Also there is no mixer.
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/440465](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/440465)

---

