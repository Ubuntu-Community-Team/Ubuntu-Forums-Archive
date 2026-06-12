---
title: "frozen bubble skipping audio"
date: 2009-06-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yoasif on 2009-06-11
anyone else seeing this? i open frozen bubble, and the music in the game constantly skips. it's very annoying... :/

---

### Post by LKjell on 2009-06-11
Try the libsdl debian all package.

---

### Post by yoasif on 2009-06-11
> **LKjell said:**
> Try the libsdl debian all package.I'm assuming you mean libsdl1.2debian-all? Just installed it, makes no difference.

---

### Post by LKjell on 2009-06-11
Welcome to the brute way of doing stuff. Close all sound related programs. Go to System => Preferences => sound and set the Music and video to Pulseaduio. If it does not work then put it to Alsa. If that does not work then put it to OSS. Now if that does *not* work then we have a problem. Now each test you do remember to install the right libsdl package. Like when you are doing pulse you have libsdl1.2debian-pulseaudio installed.

Or you can just cut all this crap and edit the /etc/pulse/daemon.conf file and mess with default-fragments,
default-fragment-size-msec. Which is likely the problem.

---

### Post by yoasif on 2009-06-11
Installing libsdl1.2debian-pulseaudio fixes the issue for me.

apt-cache policy libsdl1.2debian-pulseaudio
libsdl1.2debian-pulseaudio:
  Installed: 1.2.13-4ubuntu3
  Candidate: 1.2.13-4ubuntu3

Obviously this removes libsdl1.2debian-alsa -- is this a bug in that package?

i've filed a bug report if you guys have any insights: [https://bugs.launchpad.net/ubuntu/+source/frozen-bubble/+bug/386104](https://bugs.launchpad.net/ubuntu/+source/frozen-bubble/+bug/386104)

---

### Post by LKjell on 2009-06-12
Well sound in linux is often broken. Troubleshooting sound related problems could be annoying. The bad part using pulse with alsa is that you do not know which to blame. Did you try libsdl1.2debian-alsa with alsa? I belive it works. Then does that package contain bugs since when you switch to pulse it does not? Remember that when you are using pulse all sound go through pulse. And the libsdl just a package to tell which framework to use.

---

### Post by zenarcher on 2009-06-15
libsdl1.2debian-pulseaudio fixed the problem for me, as well.

Thanks,
zenarcher

---

### Post by yoasif on 2009-06-15
> **zenarcher said:**
> libsdl1.2debian-pulseaudio fixed the problem for me, as well.

Thanks,
zenarcher

would you mind commenting on the bug? [https://bugs.launchpad.net/ubuntu/+source/frozen-bubble/+bug/386104](https://bugs.launchpad.net/ubuntu/+source/frozen-bubble/+bug/386104)

---

### Post by zenarcher on 2009-06-16
No problem...I have done so.

Regards,
zenarcher

---

