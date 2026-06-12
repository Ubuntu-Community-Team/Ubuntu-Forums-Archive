---
title: "Can't update ubuntu 8.04 LTS"
date: 2015-07-18
forum: Installation &amp; Upgrades
---

### Post by Fernando_Resqun on 2015-07-18
Dear All:

I'm on Linux, and of course on Ubuntu. I have a really old hardware. My motherboard
is Asus A7N266 and an Athlon XP 1800+processor. So, I've just installed Ubuntu 8.04 LTS.
The memory is 1.2 GB.

I've tried to update the system with update manager but I've got an error:

"It appears I have to install 381 updates but the APT can't handle so many" 

I could install a newer distribution but I don't know which which would be the
newest that can run in my computer without getting it too slow. 

The whole idea to update ubuntu as many as possible is to use it with kodi
([www.kodi.tv](www.kodi.tv)) and make a very modest multimedia system. 

In your experience, what should I do maximize the performance of my system? 

Thank you.

Best Regards.
[h=1][/h][h=1][/h]

---

### Post by v3.xx on 2015-07-18
8.04 was a good year :)  but long dead and no longer supported.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
The new ubuntu is resource demanding and will not run or run well on old equipment.

I would suggest Lubuntu 14.04; it should run fast on your equipment.

I know nothing about kodi, but it looks interesting and going to check it out.  Thanks for that :)

---

### Post by Bucky Ball on 2015-07-18
Clean install of a supported release. 14.04 LTS is a good suggestion as it seems you don't like to upgrade your system. 14.04 LTS is supported until 2019. Good luck and post a new thread if you have any problems. We can't give you support with 8.04 LTS as it is ancient. Reached end-of-life over four years ago. :)

Also, as mentioned, you won't get much joy from Ubuntu on that machine. Lubuntu or possibly Xubuntu is your only hope. Kodi works fine in either. If you could plop another Gb of RAM in that machine things would look a lot better.

---

### Post by v3.xx on 2015-07-19
> **Bucky Ball said:**
> Kodi works fine in either.
So kodi works well.  Another plus

---

### Post by mörgæs on 2015-07-19
An Athlon XP does not have SSE2. If that's a problem please see the 'old hardware' link in my signature, especially second post in the thread.

---

### Post by Fernando_Resqun on 2015-07-19
Thank you all for the help. 


I 've just installed Lubuntu 14.04. I could perform an update with no
errors. 

The next step, I think is to install the drivers for the A7N266 motherboard. Do you
know how should I proceed to do this? 

I can't set screen resolution above 1024x768, and 4/3 aspect ratio. In windows
I can set higher resolutions with 16/9. 

Regards.

---

### Post by Bucky Ball on 2015-07-19
You don't need drivers for the motherboard. Sounds like you might need drivers for the graphics, though. As this new issue has nothing to do with the original, solved issue, I suggest you post a new thread with a descriptive title and the output of this from a terminal:

> sudo lshw -C video

Post the output on the new thread and post a link to the new thread here if you like when you mark this solved thread as 'solved' (see the first link in my signature). Thanks and good luck. :)

---

### Post by Fernando_Resqun on 2015-07-19
Sorry. I think it's the second time in my life that I use a forum.

Let's close this Tread and mark it as solved.

This would be the link to the next Thread:

[http://ubuntuforums.org/showthread.php?t=2287472](http://ubuntuforums.org/showthread.php?t=2287472)

Thanks.

Regards.

---

